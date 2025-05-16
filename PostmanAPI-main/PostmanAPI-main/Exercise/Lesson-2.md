# Exercise/Lesson 2: Áp Dụng Varibles & Postman Workflow
```javascript
==>> IMPORTANT NOTE: Hãy tạo ít nhất 1 e.g Cho mỗi request trong bài tập này
==>> để team review đỡ tốn thời gian trong quá trình chấm bài
```

## Bài tập 1: 

## [API Create new order](https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#43create-a-new-order)

```json
Tình huống: 
```
- Trong dự án QC cần thực hiện việc tạo Order thường xuyên trong quá trình implement và testing và để đa dạng data thì Yêu cầu đặt ra là Customer Name phải khác nhau (Hoặc ít được trùng lặp).  
- Spec thực tế: Customer Name tối đa 20 ký tự.

```json
Giải pháp:
```
- Tạo 1 giá trị Random cho Param `"customerName"` dùng cho mỗi lần tạo Order mới.

```json
Nhiệm vụ:
```
1.1 \- Tạo 1 Random customer name có độ dài không quá 20 ký tự và lưu vào biến môi trường và sử dụng trong khi tạo Order.

1.2 \- Sau khi tạo Order thành công lưu giá trị Order ID vào biến môi trường.

### Phân tích cách xử lý:

1\. Từ Example request body của API Create new order
→ 2 giá trị Required cần có là `CartID` và `customerName`

2\. Lấy giá trị Cart ID: 
Tìm đến API trả về giá trị của Cart ID là: [Create a cart](https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#33create-a-new-cart)
→ Set biến `cartId` từ Response của API này

3\. Quay về [API Create new order](https://github.com/st-phidao/PostmanAPI/edit/main/Exercise/Lession-2.md#api-create-new-order) gọi biến `cartId` vừa set vào Param `cartId`

```json
"cartId": "{{cartId}}"
```

4\. Tiếp đến Tại `Pre-request script`: viết script tạo Random customer name và gán vào biến `randomCustomerName` theo yêu cầu bài toán

5\. Tương tự bước 3 sau khi đã set biến `randomCustomerName` thì gọi biến tại Param `"customerName"`
```json
"customerName": "{{ramdomName}}"
```

6\. Chạy Request [Create a new order](https://github.com/st-phidao/PostmanAPI/edit/main/Exercise/Lession-2.md#api-create-new-order) → `400 Bad request`
→ Check Response body:
```json
"error": "The cart is empty."
```

7\. Tìm đến [API Add item to cart](https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#34add-an-item-to-cart) → Add any item

8\. Chạy lại Request Create a new order → Success → **Check Response body** 

→ Tạo Script để lưu Order id vào biến `orderId`

9\. Gọi các API cần thiết đã thiết lập ở trên để tạo Order và kiểm tra giá trị của biến **"orderId"**

## 2. Bài Tập 2: Tạo và làm việc với end-to-end workflow trong Postman
[API Specs
](https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#simple-grocery-store-api)
### 2.1. Create a New Client:
- Fields:
```json
{
"clientName": "{{randomName}}" //(generated from Exercise 1).
"clientMail": "{{any_email_format}}"
}
```
Note: `{{randomName}}` là random customer name generated từ Exercise 1 và đã được lưu trong environment variable.
### 2.2. Set Up 1 API Folder cho 1 Order Workflow hoàn chỉnh:
- List toàn bộ những APIs cần thiết để hoàn thành việc tạo order
- Viết scripts cần thiết cho mỗi API được list ra
- ex:
  - dùng `clientName` & `clientEmail` khi tạo client
  - Dùng `Client ID` từ API vừa tạo ở trên cho order creation API
  - Đảm bảo tất cả các variables, ex: `Order ID`, được handle và sử dụng 1 cách dynamic
- Mục đích: dynamically pass data between APIs, ensuring the creation and validation of an order end-to-end.
### 2.3. Verify Created Order Information
- Ensure that all related variables, such as Client ID and Order ID, are properly used to retrieve and display accurate information about the order
  - Using API `GET order` to check out the final result

## 3. Submit bài tập
- Tạo collection với tên `[QC_Name]_API_Lesson_2`
- Submit collection **với ĐẦY ĐỦ e.g** vào [Form](https://docs.google.com/forms/d/e/1FAIpQLSeRFabyZH_Y6jQnTC0H-_yFMzEri3TJ4Zd0fwqdu9NLDyLtqA/viewform)
- Nếu có khó khăn or feedback, hãy điền vào form & thoải mái liên hệ team sharing
