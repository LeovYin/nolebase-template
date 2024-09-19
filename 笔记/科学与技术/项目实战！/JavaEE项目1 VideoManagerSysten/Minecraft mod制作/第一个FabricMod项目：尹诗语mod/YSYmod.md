这是我从零开始学做Java版Minecraft的Mod
# 0.初步部署：用Fabric初始化你的mod
## 1.JDK21安装及环境变量

## 2.IDEA安装配置

## 3.Fabric模组模版生成
[点这里进入网站](https://fabricmc.net/develop/template/)
网站相关内容简绍：
1. Mod Name:mod的名称(id)
2. Packet Name：包名
3. Advanced Options：进阶选项
	1. 勾选Data Generation：生成原版提供的API和文件
4. Download Template

## 4.用IDEA打开解压后的文件夹

## 5.打开VPN并等待Gradle下载

## 6.打开Gradle的genSources下载原版文件

## 7.将Mod.Java的ModID提出来
```java
public static final String MOD_ID = "ysymod";  
  
public static final Logger LOGGER = LoggerFactory.getLogger(MOD_ID);
```
## 8.修改fabric.mod.json文件
1. id：改为自己mod的id
2. name：改为自己mod的名字
3. description：改为自己mod的描述
4. authors：改为作者的名字
5. contact
	1. sources：改为自己的网站
6. icon：改为自己mod的图标
7. entrypoint：
	1. 加上client：\[] "com.besson.ysymod.YSYModClient" \]
## 9.运行Minecraft Client！

`开发mod的核心方法，对照原版代码，深扒，理解，照着写`
# 1.注册一个物品
## 1.在mod文件夹中创建一个item包，并且建立Moditem的Java类

## 2.写一个Item的注册方法
```java
public static Item registerItems(String id, Item item) {  
    // register items here  
    //原始方法(复杂)
	return Registry.register(Registries.ITEM, RegistryKey.of(Registries.ITEM.getKey(), Identifier.of(YSYMod.MOD_ID,id)), item); 
	//简略方法(相对简单)
    return Registry.register(Registries.ITEM, Identifier.of(YSYMod.MOD_ID, id), item);  
}
```

## 3.写一个总的注册方法(给主类调用，让其加载到游戏中)
```java
public static void registerModItems() {  
    YSYMod.LOGGER.info("Registering Mod Items");  
}
```
在主类的 onInitialize( )方法中调用
```java
ModItems.registerModItems();
```
## 4.配置资源文件
### 资源文件夹建立
1. 打开resource/...mod
2. 新建一个lang目录，用于存放语言文件
	1. 创建en_us.json
	2. 创建zh_cn.json
3. 新建一个models文件夹用于存放模型配置及文件
4. 新建一个textures文件夹用于存放贴图文件

### 配置资源
1. 在lang文件中，编辑json文件，配置物品的名称
```json
"item.ysymod.ysy_item": "YSY "
```
2. 在models文件夹中建立一个mod物品名的json文件
```json
{  
  "parent": "minecraft:item/generated",  //渲染方式
  "textures": {  
    "layer0": "ysymod:item/ysy_item"  //材质文件
  }  
}
```
3. 将画好的贴图添加进 textures/item 文件夹中，并重命名为mod物品的名称

## 5.注册物品
1. 在ModItem.java类中注册
```java
public static final Item YSY_ITEM = registerItems("ysy_item",new Item(new Item.Settings()));
public static void addItemsToIG(FabricItemGroupEntries generator) {  
    generator.add(YSY_ITEM);  
    //在后面添加物品对象
}
```
# 2.建立一个物品栏
## 1.原版物品栏
### 1.用Fabric调用原版API将物品添置原版的物品栏中
```java
public static void addItemsToIG(FabricItemGroupEntries generator) {  
    generator.add(YSY_ITEM);  
    ...
}
```
### 2.注册物品栏
```java
public static void registerModItems() {  ItemGroupEvents.modifyEntriesEvent(ItemGroups.INGREDIENTS).register(Moditems::addItemsToIG);  //key：在原材料栏中注册物品
    YSYMod.LOGGER.info("Registering Mod Items");  
}
```
### 3.添加语言文件(en_us.json)
```json
"item.ysymod.ysy_item": "YSY "
```
### 4. 调用注册方法(在Mod的Java文件中的onInitialize()方法中)
```java
Moditems.registerModItems();
```
## 2.新建物品栏
### 1.新建一个实体类ModItemGroups
### 2.新建一个物品栏对象
```java
public static final ItemGroup YSY_GROUP =  Registry.register(Registries.ITEM_GROUP,Identifier.of(YSYMod.MOD_ID,"ysy_group")  
       , ItemGroup.create(null ,-1 ).displayName(Text.translatable("itemGroup.ysy_group"))  
                .icon(()-> new ItemStack(Moditems.YSY_ITEM))  
                .entries((displayContext, entries) ->{  
                    entries.add(Moditems.YSY_ITEM);  
                    entries.add(Blocks.BRICKS);  //这里添加物品栏物品
                }).build());
```
### 3.注册物品栏
```java
public static void registerModItemGroups() {  
    YSYMod.LOGGER.info("Registering ModItemGroups");  //因为物品栏是Java中的属性所以只需走个过场
}
```

# 3.建立一个方块
## 1.写一个方块的注册方法
```java
//先把方块注册为物品
 public static void registerBlockItems(String id, Block block) {  
    Item item= Registry.register(Registries.ITEM, Identifier.of(YSYMod.MOD_ID,id), new BlockItem(block, new Item.Settings()));  
if(item instanceof BlockItem){  
    ((BlockItem)item).appendBlocks(Item.BLOCK_ITEMS,item);  
}  
 }
 
public static Block register(String id , Block block) {  
    registerBlockItems(id, block);  
    return Registry.register(Registries.BLOCK, Identifier.of(YSYMod.MOD_ID,id),block);  
}
```
## 2.创建方块对象
```java
public static final Block YSY_BLOCK = register("ysy_block", new Block(AbstractBlock.Settings.create().strength(1.0F, 1.0F)));  

public static final Block YSY_BLOCK_ORE = register("ysy_block_ore", new Block(AbstractBlock.Settings.create().strength(4.5F, 3.0F)));  

public static final Block RAW_YSY_BLOCK = register("raw_ysy_block", new Block(AbstractBlock.Settings.create().strength(1.0F, 1.0F)));
```

## 3.注册方块
1. 在新建的类中写上注册方法(一个提示完成的方法就行)
```java
public static void registerModBlocks() {  
    YSYMod.LOGGER.info("Registering Mod Blocks");  
}
```
2. 在主类的onInitialize方法中调用
```java
ModBlock.registerModBlocks();
```

## 4.将方块添加到物品栏中
```java
entries.add(ModBlock.YSY_BLOCK);  
entries.add(ModBlock.RAW_YSY_BLOCK);  
entries.add(ModBlock.YSY_BLOCK_ORE);  
```
## 5.物品配置
1. 配置语言文件
2. 配置方块属性
	1. 新建blockstates文件夹(用于设置方块属性)
	2. 新建 `方块名.json`文件
	3. 配置json文件 
3. 配置模型文件
	1. 在models中新建block文件夹
	2. 新建 `方块名.json`文件
	3. 配置json文件
	4. 在textures中新建block文件
	5. 放入贴图素材
4. 配置方块物品贴图
	1. 在`models/item `文件夹中添加`方块名.json` 配置物品贴图

# 4.掉落物列表
1. 在resources目录下创建一个data文件夹，并依次创建`mod名`文件夹，`loot_table文`件夹，`blocks`文件夹
2. 配置方块的json属性
3. 配置方块的挖掘属性

# 5.配方