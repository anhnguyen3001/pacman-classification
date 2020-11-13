# Pacman - Classification
- Câu 1:
  + Chạy loop (i) trên tập huấn luyện (trainingData) 
  + Với mỗi loop tìm label có điểm max
  + Nếu labelMax != trainingLabel[i] (ứng với trainingData đó) thì cập nhật lại weight:
    + weight[trainingLabel[i]] += trainingData[i]
    + weight[labelMax] -= trainingData[i]
- Câu 2:
  + Sử dụng hàm sortKey của datastructer Counter để xếp weights theo thứ tự giảm dần
  + Trả về list với 100 phần tử
  + Q2: 'a'
- Câu 3:
  + Loop trên CGrid
  + Làm tưởng tự với câu 1
  + Phần cập nhật: theo phần mô tả của tài liệu
  + Check accuracy:
    + 2 vòng loop lồng nhau trên validationData -> validationLabels 
    + Tìm labelMax -> Tính tổng số labelMax = validationLabels[i]
  + Cập nhật weights = gridWeights[Cmax]
- Câu 4:
  + Chạy loop (x -> DIGIT_DATUM_WIDTH, y -> DIGIT_DATUM_HEIGHT)
    + Nếu (x, y) là khoảng trắng và chưa thăm: thêm vào thăm, gọi hàm determineWhiteRegion(), số vùng trắng += 1
  + Hàm determineWhiteRegion(): sử dụng BFS để tìm khoảng trắng liên tiếp từ vị trí hiện tại
  + Cập nhật features[số vùng trắng] = 1, còn lại features = 0
- Câu 5:
  + Tương tự câu 1
  + labelMax != trainingLabel[i]: cập nhật weight:
    + weight += trainingData[0][trainingLabel[i]]
    + weight -= trainingData[0][labelMax]
- Câu 6:
  + Tạo các features: closetGhost, closetFood, closetCapsule, remaingFood
  + Lấy trạng thái tiếp theo ứng với action
  + RemainingFood: lấy số hạt còn lại với state tiếp
  + 3 features còn lại: 
    + Lấy danh sách ứng với state tiếp theo
    + Tìm khoảng cách ngắn nhất 
    + Tính value: ( * mult: dựa vào độ quan trọng)
      + Capsule: value = 9 / khoảng cách 
      + Ghost: value = khoảng cách * 8
      + Food: value = 7 / khoảng cách 
