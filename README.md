# own-npm-lib

project này để thí nghiệm đẩy module tự chế lên npm repository.

## 1. Tạo một tài khoản npm tại http://npmjs.com

## 2. Tạo project mà bạn muốn đẩy lên npm, lấy project này làm ví dụ

- Tạo folder: `mkdir own-npm-lib`

- Nhảy vô folder làm việc: `cd own-npm-lib`

- Tạo file package.json: `yarn init -y`

- Tạo file index.js để code chức năng cho project:
```js
// index.js
export const addTwoNumber = (a, b) => a + b;
```

- Sửa file package.json để code chạy đc: ở đây dùng ES6 nên cấu hình `"type":"module"` trong package.json

```json
{
  "name": "own-npm-lib",
  "version": "1.0.2",
  "main": "index.js",
  "repository": "https://github.com/giatk/own-npm-lib.git",
  "author": "giatkt1598 <giatkt1598@gmail.com>",
  "license": "MIT",
  "type": "module" //thêm dòng này
}
```

- OK xong phần chuẩn bị project để đẩy lên npm.

## 3. Tạo git repository đẩy project vô, ko có git repository thì ko đẩy lên npm đc.

```bash
# on root folder
git init
git add .
git commit -m "first commit"
git remote add origin "your_git_repository"
git branch -M main
git push -u origin main
```

## 4. Xong khâu chuẩn bị, giờ đến khâu publish lên npm.

```bash
npm login # đăng nhập tài khoản npm zô
npm whoami # check login
```
```bash
# on root folder
npm link # thêm project vô local npm registry
npm link "name_of_package"
npm publish # đưa package lên server npm
```

## Extra: Cập nhật lib lên phiên bản mới hơn

- Sửa code sau đó push lên git.
```bash
git add .
git commit -m "message"
git push
```

- Sử dụng 1 trong 3 lệnh sau để nâng version của package, lưu ý phải push code lên git r mới sài được mấy lệnh này nha:
```bash
npm version patch # From 0.0.1 to 0.0.2
npm version minor # From 0.1.0 to 0.2.0
npm version major # From 1.0.0 to 2.0.0
```

- Dùng lệnh `npm publish` để đẩy package lên server.

### Update package phiên bản cục súc:

- Sửa version package trong 2 file **package-lock.json** và **package.json** rồi chạy lệnh `npm publish`