---
author: TrucJ
title: Nhập môn lập trình Golang
date: '2023-10-02'
description: Một bài viết mà bạn đọc xong có thể code được ngay ngôn ngữ lập trình Golang.
tags:
  - Golang
  - beginner
  - tutorial
categories:
  - Language
image: banner.png
---

__Golang__ (hay _Go_) là một ngôn ngữ lập trình không quá phổ biến trong môi trường đại học nhưng lại được sử dụng tại rất nhiều doanh nghiệp (trong đó có ZaloPay). Tuy nhiên, hiện tại chưa có nhiều tài liệu về ngôn ngữ này, đặc biệt là tài liệu tiếng Việt.

Chính vì lý do đó, mình đã biết ra blog này với mong muốn giúp đỡ các bạn có nhu cầu tìm hiểu về Golang. Mong đây là một bài viết rõ ràng và hữu ích với các bạn.

*Tái bút: Bố cục bài mình dựa theo bố cục bài giảng của thầy Nguyễn Minh Huy - giảng viên OOP của mình khi mình còn là sinh viên tại trường HCMUS, mong bố cục này sẽ dễ tiếp cận đối với các bạn*

## Các thành phần cơ bản của chương trình Golang
### Giới thiệu ngôn ngữ Golang
__Golang__ là một ngôn ngữ lập trình được phát triển bởi Google vào năm 2007 và đã được công bố chính thức vào năm 2009. Ngôn ngữ này nổi tiếng với sự đơn giản, hiệu suất cao, và hệ sinh thái mạnh mẽ.

Golang được thiết kế để tối ưu hóa việc phát triển phần mềm và xây dựng ứng dụng có độ tin cậy cao. Với cú pháp đơn giản, hệ thống quản lý bộ nhớ tự động, và các tính năng như xử lý đồng thời tích hợp, Golang rất phù hợp cho việc xây dựng hệ thống web, ứng dụng đám mây, và các ứng dụng có yêu cầu về hiệu suất và thời gian đáp ứng nhanh chóng.

Ngoài ra, cộng đồng Golang rất phát triển, với nhiều thư viện và framework mạnh mẽ, giúp những người phát triển dễ dàng xây dựng các ứng dụng đa dạng và phức tạp. Golang đã trở thành một trong những ngôn ngữ phát triển phổ biến và được sử dụng rộng rãi trong ngành công nghiệp công nghệ thông tin.

### Biến, hằng, kiểu dữ liệu
#### Biến
Để khai báo *biến*, ta sử dụng:
- Từ khoá `var`.
- Ký hiệu `:=` (trong trường hợp vừa khai báo và vừa gán giá trị).

Để gán giá trị cho biến đã được khai báo, sử dụng ký hiệu `=`.

```go
var x int       // Khai báo biến x kiểu int
x = 5           // Gán giá trị 5 cho biến x

var y int = 10  // Khai báo biến y kiểu int và
                // đồng thời gán giá trị 10 cho biến y

z := 15         // Khai báo và gán giá trị 15 cho biến z
                // (kiểu dữ liệu được tự động suy luận)
```

#### Hằng
Để khai báo hằng số, sử dụng từ khoá `const` kèm với ký hiệu `=` để gán trị của hằng.
```go
const pi = 3.14159
const author string = "TrucJ"
```

#### Kiểu dữ liệu
Go hỗ trợ nhiều kiểu dữ liệu cơ bản:
- `int`: số nguyên, kiểu `int` có kích thước khác nhau như `int8`, `int16`, `int32`, và `int64` (Mặc định `int` thường tương đương với `int32` hoặc `int64`, phụ thuộc vào nền tảng và kiến trúc của máy tính.)
- `uint`: Tương tự như `int`, nhưng chỉ cho phép lưu trữ các số nguyên không âm.
- `float32` và `float64`: Đây là kiểu dữ liệu để lưu trữ các số thực (số dấu phẩy động) với độ chính xác khác nhau. `float32` có độ chính xác thấp hơn so với `float64`.
- `string`: Kiểu dữ liệu này dùng để lưu trữ chuỗi ký tự.
- `bool`: Kiểu dữ liệu `bool` chỉ có hai giá trị là `true` và `false`.
- `byte`: `byte` thường được sử dụng để lưu trữ một ký tự ASCII hoặc dữ liệu nhị phân. Nó tương đương với `uint8`.
- `rune`: `rune` được sử dụng để lưu trữ một ký tự Unicode và tương đương với `int32`.
- `complex64` và `complex128`: Kiểu dữ liệu này cho phép bạn lưu trữ số phức, trong đó có một phần thực và một phần ảo. `complex64` sử dụng `float32` cho cả hai phần, còn `complex128` sử dụng `float64`.
- `uintptr`: Kiểu dữ liệu này được sử dụng để lưu trữ giá trị con trỏ hoặc địa chỉ bộ nhớ, thường được sử dụng trong các tình huống liên quan đến bộ nhớ không an toàn.

```go
var age int = 22
var height float32 = 1.75
var nation string = "Vietnam"
var isMale bool = true
```

### Nhập xuất
Thư viện: `import "fmt"`

#### Nhập
- `fmt.Scan()`: Nhập không có định dạng
- `fmt.Scanf()`: Nhập có định dạng

Lưu ý: Khi nhập, cần dùng `&` để truyền con trỏ của biến vào hàm

#### Xuất
- `fmt.Print()`: Xuất chuỗi không có định dạng
- `fmt.Printf()`: Xuất chuỗi có định dạng
- `fmt.Println()`: Xuất chuỗi đồng thời thêm khoảng cách vào giữa các argument và thêm xuống hàng vào cuối (tương tự như `print` trong *python*)

#### Các định dạng
- `%d`: số nguyên
- `%f`: số thực (để có đúng `x` chữ số ở phần thập phân, sử dụng `%.xf`)
- `%s`: chuỗi
- `%c`: ký tự
- `%t`: boolean
- `%b`: số nguyên dưới dạng nhị phân
- `%x` và `%X`: số nguyên dưới dạng hex
- `%p`: con trỏ
- `%v`: interface
- `%q`: chuỗi với dấu nháy kép (quote)

Ví dụ:
```go
package main

import "fmt"

func main() {
    var name string
    var age int

    fmt.Print("Nhập tên: ")
    fmt.Scanf("%s", &name)

    fmt.Print("Nhập tuổi: ")
    fmt.Scan(&age)

    fmt.Println("Xin chào", name)
    fmt.Printf("Bạn %d tuổi.\n", age)
}
```

## Cấu trúc điều khiển
### Biểu thức và toán tử
Hầu hết các biểu thức toán tử trong Go đều giống như C++
#### Toán tử số học
Các toán tử `+ - * / %` giống C++ hoàn toàn




<!-- Nhập xuất file, import, defer, go routine -->