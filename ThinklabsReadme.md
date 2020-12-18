# Build MAIN images
`cd images/ckan`  
`docker build --tag thinklabs/ckan:2.9.1localpy2 2.9py2`  
# Build DEV images
`cd images/ckan-dev`  
`docker build -t thinklabs/ckan-dev:2.9py2 -f 2.9py2/Dockerfile .`  
# Config
Chỉnh sửa ckan ini bằng cách thêm sửa vào file compose/.ckan-env
Với những config được cấu hình kiểu như sau   
- Viết hoa toàn bộ
- Thay dấu . thành 2 dấu gạch
- Ví dụ: ckan.storage_path trong file .ini sẽ tương dương với CKAN__STORAGE_PATH trong file config .ckan-env
# BUILD DEV container
`cd compose`   
`docker-compose -f docker-compose-dev.yml build`   
# RUN DEV container
`docker-compose -f docker-compose-dev.yml up`   
# STOP và xóa hết dữ liệu
`docker-compose -f docker-compose-dev.yml down -v`   
# RESTART 
`docker-compose -f docker-compose-dev.yml restart ckan`
# Cài đặt extension dev
- Copy extension vào folder compose/ckanext
- Sau khi run ckan container truy cập vào với quyền root và cài thôi:  
``docker exec -u root -it ckan /bin/bash``
Ví dụ:   
``cd src_extensions/ckanext-ckan_theme  && python setup.py develop``
- Khởi động lại ckan   
``docker-compose -f docker-compose-dev.yml down ckan``
``docker-compose -f docker-compose-dev.yml up ckan``
``docker-compose -f docker-compose-dev.yml restart ckan``

   
