查询非空数组
>db.collection_name.find({array_name:{$elemMatch:{$ne:null}}})