# ItemAttributeAPI
更輕鬆的編輯物品NBT

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
      
      
      
      
      
      
      
      
      
      
      
      
      
      
      
      
      
      
      
      
