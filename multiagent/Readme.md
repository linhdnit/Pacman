Project 2: Multi-Agent Search

Question 1: Reflex Agent
Yêu cầu: Hoàn thiện hàm evaluationFunction() để đánh giá đưa ra khả năng phản xạ tốt nhất cho pacman
Giải quyết: dựa vào khảng cách giữa pacman với thức ăn và khoảng cách giữa pacman và con ma
	Xét khoảng cách giữa pacman với thức ăn trong từng khoảng khác nhau, cho điểm đánh gia từng khoảng đó
	Sau đó kiểm tra nếu vị trí của ma có trùng với vị trí tiếp theo của pacman thì trừ điểm đánh giá
	Nếu khôgn trùng thì kiểm tra khoảng cách giữa ma với vị trí mới để đánh giá điểm
	Cuối cùng trả về Điểm + Điểm đánh giá

Question 2: Minimax
Yêu cầu: Hoàn thiện thuật toán Minimax
Giải quyết:
	Xây dựng hàm miniMax():
		Đầu tiên kiểm tra xêm game kết thúc? hoặc là độ sau thấp nhất? thì trả về hàm evaluationFunction()
		Tiếp kiểm tra tác nhân hiện tại là tác nhân cuối cùng thì giảm độ sâu
		Tạo mảng đệ quy lưu tất cả các hành động đối với tác nhân hiện tại
		Kiểm tra nếu là pacman thì trả về giá trị max của mảng còn nếu là ma thì trả về giá trị min
	Trong hàm getAction() gọi hàm miniMax()

Question 3: Alpha-Beta Pruning
Yêu cầu: Hoàn thiện thuật toán Alpha-Beta
Giải quyết:
	Xây dựng hàm alphabeta():
		Kiểm tra tac nhân truyền vào hàm lớn hơn tác nhân hiện tại thì gán tác nhân là pacman và tăng độ sâu
		Kiểm tra game kết thúc thì trả về hàm evaluationFunction()
		Tạo mảng lưu các hành hộng của tác nhân
		Nếu tác nhân là pacman thì:
			Tạo một biến v với giá trị âm vô cùng
			Duyệt tất cả các hành động
			Lấy v là max của v với kết quả trả về của hàm alphabeta với trạng thái của game(tác nhân, hành động) và tác nhân khác
			Nếu v > beta thì trả về v và gán alpha = max(alpha,v)
			Cuối cùng trả về v
		Ngược lại thì:
			Tạo v với giá trị lớn vô cùng
			Duyệt tất cả các hành động
			Lấy v là giá trị nhỏ nhất
			Nếu v < alpha thì trả về v và gán beta = min (beta, v)
			Trả về v
	Trong hàm getAction():
		Tạo v là mảng các giá trị lớn vô cùng, alpha là giá trị âm vô cùng, beta: lớn vô cùng
		Duyệt tất cả các hành động
		Lấy v = max(v, alphabeta())
		Trả về v cần tìm

Question 4:  Expectimax
Yêu cầu: Tối ưu hoá thuật toán Alpha-beta
Giải quyết:
	Xây dựng hàm expectimax():
		Kiểm tra kết thúc game hoặc độ sâu = độ sau hiện tại thì trả về hàm evaluationFuction()
		Nếu tác nhân là pac man thì:
			value : giá trị âm vô cùng
			Duyệt tất cả hành động
			Lấy trạng thái với tác nhân và hành động hiện tại
			Tạo mảng lưu expectimax với trạn thái và tác nhân khác
			value = max của mảng trên
			gán giá trị cho hành động trả về
		Ngược lại
			Nếu số ma =1 thì tăng độ sâu và đổi tác nhân tiếp theo là pacman, ngược lại đổi tác nhân
			value: giá trị lớn vô cùng
			Tiếp tục duyệt các hành động để trả lại giá trị cho v
		Cuối cùng trả lề value và hành động
	Trong hàm getAction() gọ hàm expectimax()
