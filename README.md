#mongodb-query

####1. Membuat database `academic`.

#####input :
```

use academic

```

#####output :
```

switched to db academic

```

####2. Menampilkan semua collection dan data dalam database.

#####input :
```

show collections


```

#####output :
```

department
students
system.indexes

```

####3. Membuat atau mengaktifkan database.

#####input :
```

use academic

```

#####output :
```

switched to db academic

```



####4. Membuat collection ```department```.


#####input :
```

db.createCollection("Departments");

```

#####output :
```

ok: 1


```


####5. Membuat collection  ```student```.

#####input :
```

db.createCollection("Students");

```

#####output :
```

ok: 1

```

####6. Melihat struktur collection ```student```.

#####input :
```
var schema = db.students.findOne()

```

#####output :
```
_id
nim
name
address
department
```

####7. Menginputkan 5 data ke dalam collection ```department```.

#####input :
```

db.department.insert([
	{
		code: "FTI",
		name: "Fakultas Teknologi Industri",
		major: [
				{name: "Teknik Mesin"},
				{name: "Teknik Elektro"},
				{name: "Teknik Kimia"}
				]
	},
	{
		code: "FMIPA",
		name: "Fakultas Matematika dan Ilmu Pengetahuan Alam",
		major: [
				{name: "Matematika"},
				{name: "Fisika"},
				{name: "Biologi"}
				]
	},
	{
		code: "FH",
		name: "Fakultas Hukum",
		major: [ {name: "Ilmu Hukum"} ]
	},
  {
		code: "FSRD",
		name: "Fakultas Seni Rupa Desain",
		major: [
				{name: "Desain Komunikasi Visual"},
				{name: "Desain Interior"}
				]
	},
  {
		code: "FEB",
		name: "Fakultas Ekonomi Bisnis",
		major: [
				{name: "Manajemen"},
				{name: "Ekonomi Syariah"}
				]
	}

])

```

#####output :
```

WriteResult({ "nInserted" : 3 })

```

####8. Menginputkan 3 data ke dalam collection ```student``` beserta reference ke  ```department```.

#####input :
```

db.students.insert(
  [{
    nim: 1120110001,
    name: "John Doe",
    address: "Jalan Kemang I",
    department:
      {
          "$ref" : "department",
          "$id": ObjectId("5890129c7cd7a31e0408651a"),
          "$db": "academic"
      }
  },

  {
    nim: 1220110005,
    name: "Jane Smith",
    address: "Jalan Palmerah I",
    department:
      {
          "$ref" : "department",
          "$id": ObjectId("5890129c7cd7a31e0408651a"),
          "$db": "academic"
      }
  },

  {
    nim: 1320110003,
    name: "Marrie Queen",
    address: "Jalan Senayan I",
    department:
      {
          "$ref" : "department",
          "$id": ObjectId("5890129c7cd7a31e0408651c"),
          "$db": "academic"
      }
  }]

)

```

#####output :
```

BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 3,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
})


```

####9. Melihat isi collection ```student```.

#####input :
```

db.students.find()

```

#####output :
```

{
    "_id": ObjectId("58901db17cd7a31e0408651d"),
    "nim": 1120110001,
    "name": "John Doe",
    "address": "Jalan Kemang I",
    "department": DBRef("department", ObjectId("5890129c7cd7a31e0408651a"))
} {
    "_id": ObjectId("58901db17cd7a31e0408651e"),
    "nim": 1220110005,
    "name": "Jane Smith",
    "address": "Jalan Palmerah I",
    "department": DBRef("department", ObjectId("5890129c7cd7a31e0408651a"))
} {
    "_id": ObjectId("58901db17cd7a31e0408651f"),
    "nim": 1320110003,
    "name": "Marrie Queen",
    "address": "Jalan Senayan I",
    "department": DBRef("department", ObjectId("5890129c7cd7a31e0408651c"))
}

```

####10. Menampilkan key `nama` dan `address` dalam collection `student`.

#####input :
```

db.students.find({},{name:1,address:1})


```

#####output :
```

{
    "_id": ObjectId("58901db17cd7a31e0408651d"),
    "name": "John Doe",
    "address": "Jalan Kemang I"
} {
    "_id": ObjectId("58901db17cd7a31e0408651e"),
    "name": "Jane Smith",
    "address": "Jalan Palmerah I"
} {
    "_id": ObjectId("58901db17cd7a31e0408651f"),
    "name": "Marrie Queen",
    "address": "Jalan Senayan I"
}

```

####11. Menampilkan key `studentId`, `name`, dan `address` dari data student yang mempunyai `studentId` tertentu.

#####input :
```

db.students.find({nim: 1320110003},{nim:1, name:1,address:1})

```

#####output :
```

{
    "_id": ObjectId("58901db17cd7a31e0408651f"),
    "nim": 1320110003,
    "name": "Marrie Queen",
    "address": "Jalan Senayan I"
}

```

####12. Menampilkan semua data `student` secara urut berdasarkan `name` dengan `sort`.

#####input :
```

db.students.find().sort({name:1})

```

#####output :
```

{
    "_id": ObjectId("58901db17cd7a31e0408651e"),
    "nim": 1220110005,
    "name": "Jane Smith",
    "address": "Jalan Palmerah I",
    "department": DBRef("department", ObjectId("5890129c7cd7a31e0408651a"))
} {
    "_id": ObjectId("58901db17cd7a31e0408651d"),
    "nim": 1120110001,
    "name": "John Doe",
    "address": "Jalan Kemang I",
    "department": DBRef("department", ObjectId("5890129c7cd7a31e0408651a"))
} {
    "_id": ObjectId("58901db17cd7a31e0408651f"),
    "nim": 1320110003,
    "name": "Marrie Queen",
    "address": "Jalan Senayan I",
    "department": DBRef("department", ObjectId("5890129c7cd7a31e0408651c"))
}

```

####13. Menampilkan semua data `department` secara urut berdasarkan `name` secara ascending maupun descending.

#####input :
```

db.departments.find().sort({name:1})

```

#####output :
```

{
    "_id": ObjectId("589030ba7cd7a31e04086521"),
    "code": "FEB",
    "name": "Fakultas Ekonomi Bisnis",
    "major": [{
        "name": "Manajemen"
    }, {
        "name": "Ekonomi Syariah"
    }]
} {
    "_id": ObjectId("589013a67cd7a31e0408651c"),
    "code": "FH",
    "name": "Fakultas Hukum",
    "major": [{
        "name": "Ilmu Hukum"
    }]
} {
    "_id": ObjectId("589013357cd7a31e0408651b"),
    "code": "FMIPA",
    "name": "Fakultas Matematika dan Ilmu Pengetahuan Alam",
    "major": [{
        "name": "Matematika"
    }, {
        "name": "Fisika"
    }, {
        "name": "Biologi"
    }]
} {
    "_id": ObjectId("589030477cd7a31e04086520"),
    "code": "FSRD",
    "name": "Fakultas Seni Rupa Desain",
    "major": [{
        "name": "Desain Komunikasi Visual"
    }, {
        "name": "Desain Interior"
    }]
} {
    "_id": ObjectId("5890129c7cd7a31e0408651a"),
    "code": "FTI",
    "name": "Fakultas Teknologi Industri",
    "major": [{
        "name": "Teknik Mesin"
    }, {
        "name": "Teknik Elektro"
    }, {
        "name": "Teknik Kimia"
    }]
}

```

####14. Mencari data `student` dengan `name`

#####input :
```

db.students.find({name: "Marrie Queen"})

```

#####output :
```

{
    "_id": ObjectId("58901db17cd7a31e0408651f"),
    "nim": 1320110003,
    "name": "Marrie Queen",
    "address": "Jalan Senayan I",
    "department": DBRef("department", ObjectId("5890129c7cd7a31e0408651c"))
}


```
