#/etc/hosts添加域名
sudo vim /etc/hosts
127.0.0.1 my-lab

#測試DB是否連接
curl -L 'http://my-lab/test/public/db_test.php' 
docker exec -it php php /my_projects/test/artisan migrate:status

#docker執行command
docker exec -it php php /my_projects/test/artisan migrate
docker exec -it php php /my_projects/test/artisan Record:Time 2022-06-06 00:00:00 23:59:59
docker exec -it php php /my_projects/test/artisan queue:work database --queue InsertRecod

#projects內放laravel專案
切換不同專案時需要改nginx/cong.d/laravel.conf
root /my_projects/專案名稱/public;