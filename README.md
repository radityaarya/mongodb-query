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

####2. Membuat semua collection dan data dalam database.

#####input :
```

code here

```

#####output :
```

code here

```

####3. Membuat atau mengaktifkan database.

#####input :
```

code here

```

#####output :
```

code here

```



####4. Membuat collection ```department```.


#####input :
```

code here

```

#####output :
```

WriteResult({ "nInserted" : 3 })


```


####5. Membuat collection  ```student```.

#####input :
```

code here

```

#####output :
```

code here

```

####6. Melihat struktur collection ```student```.

#####input :
```code here```

#####output :
```code here```

####7. Menginputkan 5 data ke dalam collection ```department```.

#####input :
```

db.department.insert(
	[
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
	}
	]
)

```

#####output :
```

code here

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

code here

```

#####output :
```

code here

```

####10. Menampilkan key ```nama``` dan ```address``` dalam collection ```student```.

#####input :
```

code here

```

#####output :
```

code here

```

####11. Menampilkan key ```studentId```, ```name```, dan ```address``` dari data student yang mempunyai ```studentId``` tertentu.

#####input :
```

code here

```

#####output :
```

code here

```

####12. Menampilkan semua data ```student``` secara urut berdasarkan ```name``` dengan ```sort```.

#####input :
```

code here

```

#####output :
```

code here

```

####13. Menampilkan semua data ```department``` secara urut berdasarkan ```name``` secara ascending maupun descending.

#####input :
```

code here

```

#####output :
```

code here

```

####14. Mencari data ```student``` dengan ```name```

#####input :
```

code here

```

#####output :
```

code here

```
