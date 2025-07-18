# Website Dòng Họ Nguyễn

Chào mừng bạn đến với **Website Dòng Họ Nguyễn**, một dự án front-end sử dụng **ReactJS** để lưu giữ và chia sẻ thông tin về dòng họ, tập trung vào việc tưởng nhớ tổ tiên qua gia phả, ngày giỗ, vị trí mộ phần, và ảnh thờ/mộ phần. Dự án này được thiết kế đơn giản, dễ sử dụng, và mang đậm nét văn hóa Việt Nam, nhằm gắn kết con cháu và lưu giữ truyền thống gia đình.

## Mục tiêu dự án

Website được xây dựng để:
- Lưu giữ **cây gia phả** của dòng họ Nguyễn, từ tổ tiên đến các nhánh con cháu.
- Hiển thị **timeline ngày giỗ** trong năm, giúp con cháu dễ dàng theo dõi các dịp cúng giỗ.
- Cung cấp **bản đồ** vị trí mộ phần của các cụ, tích hợp Google Maps.
- Trưng bày **ảnh thờ và mộ phần** để tưởng nhớ và lưu giữ ký ức.
- Đảm bảo giao diện thân thiện, dễ dùng cho mọi lứa tuổi, đặc biệt là người lớn tuổi trong dòng họ.

Dự án sử dụng dữ liệu tĩnh (JSON), không cần backend, dễ bảo trì và mở rộng.

## Tính năng chính

1. **Cây Gia Phả**:
   - Hiển thị sơ đồ gia phả dạng cây, hỗ trợ zoom, kéo thả.
   - Click vào từng người để xem thông tin chi tiết (tên, ngày sinh, ngày mất, tiểu sử).
2. **Timeline Ngày Giỗ**:
   - Liệt kê các ngày giỗ trong năm, đánh dấu ngày đã qua và sắp tới.
   - Hỗ trợ tìm kiếm hoặc lọc theo tháng.
3. **Bản Đồ Mộ Phần**:
   - Tích hợp Google Maps, hiển thị vị trí mộ phần dựa trên tọa độ (lat/lon).
   - Marker trên bản đồ kèm thông tin cơ bản của từng cụ.
4. **Ảnh Thờ & Mộ Phần**:
   - Lưới ảnh hiển thị ảnh thờ và mộ phần, hỗ trợ phóng to và xem chi tiết.

## Công nghệ sử dụng

- **ReactJS**: Framework chính để xây dựng giao diện.
- **Tailwind CSS**: Style nhanh, hiện đại, dễ tùy chỉnh.
- **D3.js**: Vẽ sơ đồ cây gia phả.
- **Google Maps API**: Hiển thị bản đồ vị trí mộ phần.
- **JSON**: Lưu trữ dữ liệu tĩnh (thông tin gia phả, ngày giỗ, tọa độ, ảnh).

## Cấu trúc dữ liệu (JSON)

Dữ liệu được lưu trong file `src/data/familyData.json` với cấu trúc như sau:

```json
[
  {
    "id": "nguyen-van-a",
    "name": "Nguyễn Văn A",
    "age": 85,
    "birthDate": "01/01/1900",
    "deathDate": "15/03/1985",
    "lifespan": 85,
    "relationships": {
      "parent": null,
      "children": ["nguyen-van-b", "nguyen-van-c"],
      "spouse": "nguyen-thi-x"
    },
    "description": "Tổ tiên đời thứ nhất, sáng lập dòng họ.",
    "location": {
      "lat": 21.0285,
      "lon": 105.8542
    },
    "images": {
      "portrait": "path/to/portrait1.jpg",
      "grave": "path/to/grave1.jpg"
    }
  }
]
```

- **id**: Mã định danh duy nhất (string).
- **name**: Tên đầy đủ của cụ.
- **age**: Tuổi tại thời điểm mất.
- **birthDate/deathDate**: Ngày sinh/mất, định dạng `DD/MM/YYYY` (hỗ trợ âm lịch/dương lịch).
- **lifespan**: Số năm hưởng thọ.
- **relationships**: Liên kết gia đình (cha mẹ, con cái, vợ/chồng).
- **description**: Tiểu sử hoặc mô tả.
- **location**: Tọa độ vĩ độ (lat) và kinh độ (lon) của mộ phần.
- **images**: Đường dẫn đến ảnh thờ và mộ phần.

## Hướng dẫn cài đặt và chạy project

### Yêu cầu
- Node.js (v16 hoặc cao hơn)
- Trình duyệt hiện đại (Chrome, Firefox, Edge)
- Google Maps API Key (đăng ký tại [Google Cloud Console](https://console.cloud.google.com/))

### Cài đặt
1. Clone repository về máy:
   ```bash
   git clone https://github.com/your-username/family-website.git
   cd family-website
   ```
2. Cài đặt dependencies:
   ```bash
   npm install
   ```
3. Cấu hình Google Maps API Key:
   - Tạo file `.env` trong thư mục gốc.
   - Thêm dòng: `REACT_APP_GOOGLE_MAPS_API_KEY=your-api-key`.
4. Cập nhật dữ liệu:
   - Chỉnh sửa file `src/data/familyData.json` để thêm thông tin dòng họ.
   - Đảm bảo đường dẫn ảnh (portrait, grave) đúng định dạng.

### Chạy project
```bash
npm start
```
- Mở trình duyệt tại `http://localhost:3000` để xem website.

### Triển khai
- Đẩy lên **Netlify** hoặc **Vercel** để host miễn phí.
- Đảm bảo file JSON và ảnh được đẩy lên cùng repository hoặc host trên dịch vụ như Cloudinary.

## Cấu trúc thư mục

```
family-website/
├── public/
│   ├── index.html
│   └── assets/             # Ảnh thờ, mộ phần
├── src/
│   ├── data/
│   │   └── familyData.json # Dữ liệu dòng họ
│   ├── components/
│   │   ├── Navbar.js
│   │   ├── FamilyTree.js
│   │   ├── Timeline.js
│   │   ├── Map.js
│   │   └── Photos.js
│   ├── App.js
│   ├── index.js
│   └── styles/
│       └── tailwind.css
├── .env                    # Cấu hình API Key
├── package.json
└── README.md
```

## Hướng dẫn đóng góp

1. Fork repository và tạo branch mới:
   ```bash
   git checkout -b feature/your-feature
   ```
2. Thêm tính năng hoặc sửa lỗi, đảm bảo giữ nguyên cấu trúc JSON.
3. Commit và push:
   ```bash
   git commit -m "Thêm tính năng XYZ"
   git push origin feature/your-feature
   ```
4. Tạo Pull Request trên GitHub.

### Gợi ý đóng góp
- Thêm tính năng tìm kiếm theo tên cụ hoặc ngày giỗ.
- Tích hợp lịch âm (dùng `lunar-javascript`).
- Cải thiện giao diện mobile (responsive design).
- Thêm slideshow cho ảnh thờ/mộ phần.

## Thông tin liên hệ

- **Người quản trị**: [Your Name]
- **Email**: [your-email@example.com]
- **GitHub**: [your-username]

Cảm ơn bạn đã quan tâm đến dự án! Hãy cùng nhau lưu giữ và lan tỏa truyền thống dòng họ Nguyễn. 🙏