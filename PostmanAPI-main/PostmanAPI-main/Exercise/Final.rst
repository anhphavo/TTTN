**********************
Final Round
**********************

.. contents:: Table of Contents
   :depth: 3
   :local:
   :backlinks: top

.. sectnum::
   :depth: 3

``Simple Grocery Store API``
============================

``Specs:`` `Simple Grocery Store API <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst>`_

Lưu Ý: Hãy sử dụng lại collection của bài tập 2 để có đầy đủ các API cần cho việc tạo order mà không bị các lỗi thiếu product/cartid                             
                              
API Client
----------
``Specs:`` `Register New Client <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#51register-a-new-api-client>`_

Client name
~~~~~~~~~~~

Giả định requirement từ specs
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Customer Name tối đa 17 ký tự

Yêu cầu: tại API Client Create
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- Tạo 1 giá trị Random cho trường ``clientName`` dùng cho mỗi lần tạo client mới với:
    - Tối đa 17 ký tự theo specs nêu trên
    - Vì là name nên hãy tạo 1 client name theo format: ``YourName_Test_{random number}`` với ``random number`` sao cho tổng số ký tự luôn nhỏ hơn or bằng 17
    - Example:
        - Valid name: ``Phi_Test_1234``, ``Phi_Test_1002``...
        - Invalid name: ``Phi_Test_123819238012912312312``...
                              
Client email
~~~~~~~~~~~~

Giả định requirement từ specs
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Địa chỉ email có chứa tên của client name nêu trên
- Format: ``yourname_test{random 5 numbers}@example.com`` với ``random 5 numbers`` là 5 số được lấy ngẫu nhiên

Yêu cầu: tại API Client Create
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Tạo địa chỉ email có format match với requirement từ specs nêu trên
- Format: ``yourname_test{random 5 numbers}@example.com``
- Example:
    - Valid email: ``phi_test13412@example.com``
    - Invalid email: ``phi_test1223123@example.com``
- Tạo ``e.g`` sau khi hoàn thành.

API Create an Order
-------------------
``Specs:`` `Create an Order <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#43create-a-new-order>`_

Customer name
~~~~~~~~~~~~~

Yêu cầu: tại API Create an Order
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Sử dụng lại ``clientName`` đã tạo ở `1.1.1 <https://github.com/st-phidao/PostmanAPI/blob/main/Exercise/Final.rst#111client-name>`_ cho trường ``customerName`` trong request body
- Ở trường ``comment``, sử dụng lại ``clientName`` & ``clientEmail`` đã tạo ở `1.1 <https://github.com/st-phidao/PostmanAPI/blob/main/Exercise/Final.rst#11api-client>`_
    - Format: ``"comment": "clientName & clientEmail"``
    - Example: ``"comment": "Phi_Test_1234 & phi_test_12345@example.com"``

API Get Single Order
-------------------
``Specs:`` `Get Single Order <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#42get-a-single-order>`_

Verify data
~~~~~~~~~~~

Yêu cầu: tại API Get Single Order
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- Viết Test Script kiểm tra clientName & clientEmail từ response body của trường ``comment`` có sử dụng đúng data đã tạo từ Client API or API Create an Order hay không
- Tạo ``e.g.`` sau khi hoàn thành

API Add Item To Cart
--------------------
``Specs:`` `Add Item To Cart <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#34add-an-item-to-cart>`_

Auto run pre-request
~~~~~~~~~~~~~~~~~~~~

- Sau mỗi lần add cart, product đã được add sẽ không thể add lại, dẫn tới ``404/400 error``
- Dẫn tới việc trước mỗi lần add cart, phải tạo trước cart mới từ `API Create New Cart <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#33create-a-new-cart>`_
- Hãy giải quyết issue này bằng cách:
    - Tại API Add Item To Cart, viết script để gọi `API Create New Cart <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#33create-a-new-cart>`_ trước mỗi lần call `API Add Item To Cart <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst#34add-an-item-to-cart>`_ ==> nhờ đó có thể tự động tạo cart mà không cần run manual
    - Tạo ``e.g.`` sau khi hoàn thành

``Valentine's Book List API``
=============================
``Specs:`` `Valentine's Book List <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/valentines-book-list.md#valentines-book-list-api>`_

Test Script - ``200 Success``
-----------------------------
- Đọc specs & import vào postman sao cho status của API trả về là 200 & filter book data với query param ``"list"`` là``fiction``
- Viết Test Script:
    - Verify status code expected là 200
    - Verify Response có: ``"status": "OK"``
    - Verify Response có array ``results`` (không cần check trong ``results`` có gì, chỉ cần check có sự xuất hiện của mảng results)
    - Verify info của book trả về thuộc category ``fiction`` đã call trước đó
    - Tạo ``e.g.`` lưu lại tất cả những cases đã làm

Test script - ``400 Bad Request``
---------------------------------
- Viết Test Script:
    - Verify status code expected là 400
          - Tạo ``e.g.`` cho trường hợp ``failed`` test case đã viết script
          - Tạo ``e.g.`` cho trường hợp ``passed`` test case đã viết script
    - Verify nội dung của message trả về trong response có đúng với `specs defined <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/valentines-book-list.md#400-bad-request>`_ hay không
        - ``error-string``
        - ``errorcode``
        - Tạo ``e.g.`` sau khi hoàn thành

Test script - ``401 Unauthorized``
----------------------------------
- Viết Test Script:
    - Verify status code expected là 401
          - Tạo ``e.g.`` cho trường hợp ``failed`` test case đã viết script
          - Tạo ``e.g.`` cho trường hợp ``passed`` test case đã viết script
    - Verify nội dung của message trả về trong response có đúng với `specs defined <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/valentines-book-list.md#401-unauthorized>`_ hay không
        - ``error-string``
        - ``errorcode``
        - Tạo ``e.g.`` sau khi hoàn thành

Test script - Schema Validation
-------------------------------
- Đọc specs & import vào postman sao cho status của API trả về là 200 & filter book data với query param ``"list"`` là ``non-fiction``
- Viết Test Script:
    - Verify Schema của response trả về theo `response example <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/valentines-book-list.md#200-success>`_ đã được define trong specs
    - Tạo ``e.g.`` sau khi hoàn thành

``Bonus Excercise`` (Optional)
=============================
  
Bài này là optional, nếu thích có thể làm, nếu không thích xin hãy bỏ qua

``Specs:`` `Simple Grocery Store API <https://github.com/st-phidao/PostmanAPI/blob/main/Specs/simple-grocery-store-api.rst>`_

- Tạo 1 API folder và viết Script cho các API phục vụ cho việc tạo 1 Order chứa nhiều sản phẩm trong 1 lần chạy.
- Tạo thành công 1 Order với 5 sản phẩm ngẫu nhiên trong list product (Đề chọn 1 case trong các case thực tế bạn phải test)
- Kiểm tra order vừa tạo đã xuất hiện trong All order list (Trả về test result Pass or Failed)

Submit Excercise
=============================
- Tạo collection với tên ``[QC_Name]_API_Lesson_3``
- Submit collection với ĐẦY ĐỦ ``e.g`` vào `Form <https://docs.google.com/forms/d/e/1FAIpQLScQtvYCQK2MGIHfHwUiYNLRcU9UcyDXPjM1kHZ41_J4L8UvRQ/viewform>`_
- Nếu có khó khăn or feedback, hãy điền vào form & thoải mái liên hệ team sharing
- Lưu ý khi nộp bài:
      - Nếu có nhiều hơn 2 files, hãy zip file lại và gửi 1 file duy nhất để dễ quản lý
      - Hãy tự giác thêm đầy đủ các API cần thiết cho flow tạo order
      - Trước khi nộp bày, hãy tự import file mình sắp nộp để chắc chắn rằng các file không bị trống or lỗi
      - Chỉ nộp collection liên quan tới bài tập, đừng nộp history run







