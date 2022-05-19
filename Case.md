# My Photos
My Photos is an android application to store photo in cloud for free and safe. You could find it too on [github](https://github.com/danangwijaya750/ITSSB-DIY-2022-MobileCase/blob/main/Case.md)

# Screen

## Login
![Login](https://lh3.googleusercontent.com/pw/AM-JKLVgRCpuJIpPrR_gy3utBQag4VMCMPvSMcmhG_hvGuoRhnOthhLkIYryPcqwx8R7QXerl3K2lHCLQW_SdcVRJCUQN6D77CPCXz4VSZCitqoPelHyzmClQShoY7f6YDc_lXPCcnN-0YmJGgwKj1JUv7kK=w321-h649-no)

Use appropriate input type for each fields. Show error message if [Login API](###Login) returns error. Save access token from [Login API](###Login) for all API endpoints.  Redirect to login page whenever the access token is expired or API request fails with unauthorized (http status code 401). Show errors from API whenever login request isn't succeed.

## Register
![Register](https://lh3.googleusercontent.com/pw/AM-JKLVpxD4LiHezSxxKtsbBfv-WQ4Y0fCj9IhrpUkSE_4D-UnC8fSA7Y1P8lKtKx3ftJcbBc52eP-SgCJFYktcYF0YVx8xj3SnF35ipK2JJkmk6ftttSl-A720Qx6TbXXaAqhvv9toTcrPTiv-AH4aeHED9=w322-h649-no)

You can access this menu by click register button on [Login Page](##Login). Use appropriate input type for each fields. User should have password length must be greater than 8 and mixes of lowercase & uppercase characters, numeric & symbols and must match with confirm password field. Show errors from API whenever login request isn't succeed


## Homescreen
![Homescreen](https://lh3.googleusercontent.com/pw/AM-JKLWu6lJr5KuEUNA8YzHbUVeF1mltYGvJ5cecktfNT6t75_U3ki5VlafZ_0z3YwnTaBOFNp5-50TfWAWVglXvyL3cOWj4sE6h5QQ_TPx6TscjugeTYEPYrnlixnzU9sYEHLgQ22H8LhbweEdAH0zc7pC7=w348-h649-no)

You can access this page after login or user has logged in before. Page divided into 2 parts, the first one is album list, second one is photos list. Show and animate `upload photo` & `create album` button whenever `+` floating button clicked by user.
![Button Animation](https://lh3.googleusercontent.com/pw/AM-JKLWfUlWJNyG0FncFfONXGYah2orxyWz3IChBs5YarQQ5eiy9fKxIl3rCS3RfxHhlovbSKOTv8m9lILm9qcPiDFGnoCoMzTS8D8o5MqPMVY6k8r_neW_Q_lokL36s4gkJM5IJJAMP7N0-f1YVZnxTHjVq=w623-h1314-no)

### Album list
Get album list from [Album List API](###AlbumList) Show folder icon and album name beside it.

### Photo List
Get photo list from [Photo List API](###PhotoList) and show it in grid with 2 columns. Show photo above the name. Show loading icon before image loaded. Load image from internet shouldn't block users from doing anything

## Create Album
![CreateAlbum](https://lh3.googleusercontent.com/pw/AM-JKLVddRicVTAdDUmSbApvvJOMmkAxvSncmZHLpDgwulQMDLKtqh1yxqBiDlsGyUiU0rMSpA49RfV7CIxL34co1_kUa4Tf4keT79QBmmwJBENU_UuasePBpxaYuJRQpFF2YqvW2ornZrIiX1DUYcoEaGdn=w351-h650-no)

Show dialog to input album name. Call [Create Album API](###CreateAlbum) when user click button `create`. Navigate users to album page when album successfully created

## Upload Photo
![Upload Photo](https://lh3.googleusercontent.com/pw/AM-JKLUe9N3mPKEAtz1xDNCyrBRw6rly_P3UiDlhfV9cxy8ujBHH9-Eoq6zSOWIDpR5Ha5-92MLcG9N0HO_VByvHC6QF6PcBK5yVltYxoWRMHoDvYxj6XGq-A9_uR1BXTb4vC9PtwQ1xTXLWenNWw4T9VDVN=w322-h649-no)

User can access this page after click upload photo on floating button. Show name inside the page. User can choose photo and upload it to [Upload Photo API](###UploadPhoto)

## Album
![Album](https://lh3.googleusercontent.com/pw/AM-JKLXbSPaJP5pntqLWh6YeqQB80NvmVzGWMJlQ093rsM-HgdA13THtCzYTwxPLYE1eP0kEY2UCNyVNRqCjyFugEkQiiPc2N-WQ1gHD2-xLjjZIwsKpEwEjc5VHXRPo5TI0r3_F93NgF8E0zzC4R3m1f_lO=w348-h649-no)

You can access this page by click on one of the albums on the homescreen. Show album name above photo list. Download image to device when user click to one of the photo in the list.

# API
Use this host for all endpoints
```
https://api.galeri.infiniteuny.id/api/
```

## Auth
### Login
- Path: `/auth/login`
- Method: `POST`
- Request Body:
  1. email
  2. password
- Heades:
  1. `Accept` = `application/json`
  2. `Content-Type` = `application/json`
- Response:
  1. signature
 
  Sample:
  - Request:
  ```curl
  curl -L -X POST 'https://api.galeri.infiniteuny.id/api/auth/login' \
      -H 'Accept: application/json' \
      -H 'Content-Type: application/json' \
      --data-raw '{
          "email": "wahyudi@mail.com",
          "password": "12345678"
      }'
  ```
  - Response:
  ```json
    {
    "data": {
        "signature": "4|sac5wBkrixSKh2OcSArd5ftSxIEQGtEwWSXPWR2q"
    }
  }
  ```
### Register
- Path: `/auth/register`
- Method: `POST`
- Request Body:
  1. username
  2. Email
  3. password
  4. password_confirmation
- Heades:
  1. `Accept` = `application/json`
  2. `Content-Type` = `application/json`    
 
  Sample:
  ```curl
  curl -L -X POST 'https://api.galeri.infiniteuny.id/api/auth/register' \
      -H 'Accept: application/json' \
      --data-raw '{
          "name": "Wahyudi",
          "email": "wahyudi@mail.com",
          "password": "12345678",
          "password_confirmation": "12345678"
      }'
  ```
  - Response:
  ```json
    {
    "data": {
        "name": "Wahyudi",
        "email": "wahyudi@mail.com",
        "updated_at": "2022-05-18T11:29:37.000000Z",
        "created_at": "2022-05-18T11:29:37.000000Z",
        "id": 1
    }
}
  ```

### Get Users
- Path: `/user`
- Method: `GET`
- Heades:
  1. `Accept` = `application/json`
  2. `Content-Type` = `application/json`   
  3. `Authorization` = `bearer {signature}` 
- Response (array):
  1. id
  2. name
  3. email
 
  Sample:
  - Request:
  ```curl
  curl -L -X GET 'https://api.galeri.infiniteuny.id/api/user' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 4|sac5wBkrixSKh2OcSArd5ftSxIEQGtEwWSXPWR2q'
  ```
  - Response:
  ```json
    {
    "id": 1,
    "name": "Wahyudi",
    "email": "wahyudi@mail.com",
    "email_verified_at": null,
    "created_at": "2022-05-18T11:29:37.000000Z",
    "updated_at": "2022-05-18T11:29:37.000000Z"
    }
  ```

## Album
### AlbumList
- Path: `/user/album`
- Method: `GET`
- Headers:
  1. `Accept` = `application/json`
  2. `Authorization` = `bearer {signature}` 
- Response (array):
  1. id
  2. name

  Sample:
  - Request:
  ```curl
  curl -L -X GET 'https://api.galeri.infiniteuny.id/api/user/album' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 4|sac5wBkrixSKh2OcSArd5ftSxIEQGtEwWSXPWR2q'
  ```
  - Response:
  ```json
  {
      "data": [
          {
              "id": 1,
              "user_id": "1",
              "name": "Sekolah Dasar",
              "created_at": "2022-05-18T11:59:10.000000Z",
              "updated_at": "2022-05-18T11:59:10.000000Z"
          }
      ]
  }
  ```

### CreateAlbum
- Path: `/album`
- Method: `POST`
- Request Body:
  1. name
- Heades:
  1. `Accept` = `application/json`
  2. `Content-Type` = `application/json`  
  3. `Authorization` = `bearer {signature}`   
- Response:
  1. id
  2. name
  3. user
 
  Sample:
  - Request:
  ```curl
  curl -L -X POST 'https://api.galeri.infiniteuny.id/api/album' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 4|sac5wBkrixSKh2OcSArd5ftSxIEQGtEwWSXPWR2q' \
    -H 'Content-Type: application/json' \
    --data-raw '{
        "name": "Sekolah Dasar"
    }'
  ```
  - Response:
  ```json
    {
      "data": {
          "name": "Sekolah Dasar",
          "user_id": 1,
          "updated_at": "2022-05-18T11:59:10.000000Z",
          "created_at": "2022-05-18T11:59:10.000000Z",
          "id": 1
      }
    }
  ```
 
## Photo

### PhotoList
- Path: `/user/photo`
- Method: `GET`
- Query:
  1. album_id (opt) - album id
- Headers:
  1. `Accept` = `application/json`
  2. `Authorization` = `bearer {signature}` 
- Response (array):
  1. id
  2. album
  3. name
  4. size (in bytes)
  5. created_at, updated_at (timestamp)
  6. image

  Sample:
  - Request:
  ```curl
  curl -L -X GET 'https://api.galeri.infiniteuny.id/api/user/photo?album_id=1' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 4|sac5wBkrixSKh2OcSArd5ftSxIEQGtEwWSXPWR2q'
  ```
  - Response:
  ```json
  {
      "data": [
          {
              "id": 1,
              "user_id": "1",
              "album_id": "1",
              "name": "Jawaban.png",
              "size": "175090",
              "created_at": "2022-05-18T12:03:22.000000Z",
              "updated_at": "2022-05-18T12:03:22.000000Z",
              "url": "https://api.galeri.infiniteuny.id/api/photo/1"
          },
          {
              "id": 2,
              "user_id": "1",
              "album_id": "1",
              "name": "gotoubun-bg-1.jpg",
              "size": "89386",
              "created_at": "2022-05-18T12:49:51.000000Z",
              "updated_at": "2022-05-18T12:49:51.000000Z",
              "url": "https://api.galeri.infiniteuny.id/api/photo/2"
          },
          {
              "id": 3,
              "user_id": "1",
              "album_id": "1",
              "name": "gotoubun-bg-1.jpg",
              "size": "89386",
              "created_at": "2022-05-18T12:52:27.000000Z",
              "updated_at": "2022-05-18T12:52:27.000000Z",
              "url": "https://api.galeri.infiniteuny.id/api/photo/3"
          },
          {
              "id": 4,
              "user_id": "1",
              "album_id": "1",
              "name": "gotoubun-bg-1.jpg",
              "size": "89386",
              "created_at": "2022-05-18T12:52:35.000000Z",
              "updated_at": "2022-05-18T12:52:35.000000Z",
              "url": "https://api.galeri.infiniteuny.id/api/photo/4"
          }
      ]
  }
  ```

### UploadPhoto
- Path: `/photo`
- Method: `POST`
- Request Body:
  1. album - album id
  2. image - file
- Heades:
  1. `Accept` = `application/json`
  2. `Content-Type` = `multipart/form-data`    
 
  Sample:
  - Request:
  ```curl
  curl -L -X POST 'https://api.galeri.infiniteuny.id/api/photo' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 4|sac5wBkrixSKh2OcSArd5ftSxIEQGtEwWSXPWR2q' \
    -F 'album_id="1"' \
    -F 'photo=@"/home/nartos/Pictures/gotoubun-bg-1.jpg"'
  ```
  - Response:
  ```json
    {
    "data": {
        "album_id": "1",
        "user_id": 1,
        "name": "gotoubun-bg-1.jpg",
        "size": 89386,
        "updated_at": "2022-05-18T12:49:51.000000Z",
        "created_at": "2022-05-18T12:49:51.000000Z",
        "id": 2
    }
  }
  ```

## Postman Link
[Postman collection](https://www.getpostman.com/collections/5d8ff4ddaa544f189394)