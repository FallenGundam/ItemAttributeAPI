# ItemAttributeAPI
更輕鬆的編輯物品NBT  
提供 texture skull itemflag attributes NbtTag api  
![image](https://user-images.githubusercontent.com/54828956/228903732-ddf0f5b1-773c-40a8-a587-910de62605b5.png)

# required plugins:
    skript 2.6  
    skript-reflect
    NBT API
    
# API:  
    * 物品序列化
      物品轉字串，如果需要用到sql儲存物品這很好用
      效率也比yamlconfiguration更優
      nbt_ItemToString(item:item) :: string:
      nbt_StringToItem(str:string) :: item:
        ex: set {_string} to nbt_ItemToString(player's tool)
        
    * 物品自定義NBTTag
      如果想要儲存一些簡單資料可用此功能,目前可以存字串跟數字
      物品是否有某個tag
      
      item_hasNBTTag(i:item,tag:string) :: boolean:  
      
      > 獲取物品的某個tag的值
      item_getNBTTag(i:item,tag:string) :: string:   
        ex: set {_tag} to item_getNBTTag(player's tool,"mytag")
        
      > 添加tag
      item_addNBTTag(i:item,tag:string,value:object) :: item:
        ex: set player's tool to item_addNBTTag(player's tool,"mytag","hello world")  
        
      > 設置某個tag的值
      item_setNBTTag(i:item,tag:string,value:object) :: item:
        
      > 刪除某個tag的值  
      item_removeNBTTag(i:item,tag:string) :: item:
      
    * 自定義頭顱
       可使用texture value來或去頭顱
       owner 為頭顱擁有者 可不填，也可填玩家名
       Item_getSkull(texturestring:string,owner:string = "player") :: item:
         ex:
         set {_texture} to "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZGM2ZGM2YTE1M2UyYTA2MzJmMDQ2MjEzMzFjNWE5OTE3YTYyMDkxNjBhYjdiYjFmYjJhYzYxNmE0NTQ2OTEzNiJ9fX0="
         give Item_getSkull({_texture}) to player
         
    * 物品 hideflags
       flag list: https://helpch.at/docs/1.16.5/org/bukkit/inventory/ItemFlag.html 
       
       Item_HasFlag(item:item) :: boolean:
       Item_getFlags(item:item) :: strings:
       Item_addFlag(item:item,flag:string) :: item:
       Item_removeFlag(item:item,flag:string) :: item:
       
    * 物品 Attributes
      slot type: mainhand, offhand, head, chest, legs, feet
      attribute type: https://helpch.at/docs/1.16.5/org/bukkit/attribute/Attribute.html
      attribute type: 可以不用加 generic
      
      # 物品是否有attribute
      Item_HasAttribute(item:item) :: boolean:
      
      # 獲取某個slot的該屬性數值
      Item_Attribute_getValue(item:item,att:string,slot:string="mainhand") :: number:
      
      # 獲取有添加屬性的所有slot
      Item_Attribute_getAllSlot(item:item) :: strings:
      
      # 獲取該slot的所有屬性與值
      Item_Attribute_getSlotValue(item:item,slot:string = "mainhand") :: strings:
      
      # 刪除全部屬性
      Item_Attribute_clearAll(item:item) :: item:
      
      # 刪除某個slot的屬性
      Item_Attribute_clearSlot(item:item,slot:string = "mainhand") :: item:
      
      # 設定某個slot的某個屬性的值
      Item_Attribute_setValue(item:item,att:string,value:object,slot:string = "mainhand") :: item:
      
      # 添加屬性到某個slot  all代表所有slot
      Item_Attribute_addValue(item:item,att:string,Amount:number,slot:string = "all",Operation:integer = 0) :: item:
        > Operation 0, 1, 2 預設0  1跟2是代表數值會以%表示
      
      # 刪除某個slot的屬性  all代表所有slot
      Item_Attribute_removeValue(item:item,att:string,slot:string = "all") :: item:
      
      
      example:
        set player's tool to Item_Attribute_addValue(player's tool,"attack damage",10,"mainhand",0)
        
        
        
      
