gogo:
	sudo systemctl stop nginx
	sudo systemctl stop isubata.ruby.service
	ssh isucon7-q-c "sudo systemctl stop isubata.ruby.service"
	ssh isucon7-q-b "sudo systemctl stop mysql"
	sudo truncate --size 0 /var/log/nginx/access.log
	sudo truncate --size 0 /var/log/nginx/error.log
	sudo truncate --size 0 /var/log/mysql/slow.log
	scp app.rb isucon7-q-c:/home/isucon/isubata/webapp/ruby
	ssh isucon7-q-b "sudo systemctl start mysql" 
	sudo systemctl start isubata.ruby.service
	ssh isucon7-q-c "sudo systemctl start isubata.ruby.service"
	sudo systemctl start nginx
	sleep 6
	$(MAKE) bench

bench:
	ssh isucon7-q-bench "cd /home/isucon/isubata/bench && make bench"
alp:
	sudo cat /var/log/nginx/access.log | alp ltsv --format=md -m='/fonts/.*,/icons/.*,/channel/[0-9]+,/history/[0-9]+' --sort sum
