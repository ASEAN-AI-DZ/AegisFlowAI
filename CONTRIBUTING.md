# Hướng dẫn đóng góp

Cảm ơn bạn đã quan tâm đến việc đóng góp cho AegisFlow AI! 

## Các cách đóng góp

1. Báo cáo lỗi (Bug reports)
2. Đề xuất tính năng mới (Feature requests)
3. Sửa lỗi và cải thiện code
4. Cải thiện tài liệu
5. Cải thiện các mô hình học máy (AI Models)

## Quy trình làm việc với code

### Chuẩn bị môi trường
1. Fork repository
2. Clone repository đã fork về máy local
3. Cài đặt các công cụ cần thiết:
   - Composer & PHP 8.2+ (cho Backend Laravel)
   - Node.js & npm (cho Frontend Vue.js)
   - Python 3.9+ & pip (cho AI Service)
   - PostgreSQL & PostGIS (Database) hoặc sử dụng Docker Compose
   - VS Code với các extensions cho PHP/Python/Vue

### Phát triển
1. Tạo branch mới cho tính năng/fix:
   `bash
   git checkout -b feature/ten-tinh-nang
   # hoặc
   git checkout -b fix/issue-number
   `

2. Viết code và test:
   - Tuân thủ coding style của từng ngôn ngữ
   - Test kỹ trước khi commit
   - Viết test cases nếu cần thiết

3. Commit changes:
   `bash
   git add .
   git commit -m "feat/fix: mô tả ngắn gọn"
   `

4. Push và tạo Pull Request:
   `bash
   git push origin feature/ten-tinh-nang
   `

### Review process
1. Maintainers sẽ review PR của bạn
2. Có thể cần chỉnh sửa theo yêu cầu
3. Sau khi được approve, PR sẽ được merge

## Test

### Backend (Laravel)
`bash
cd backend
php artisan test
`

### AI Core (Python)
`bash
cd ai-service
pytest
`

### Frontend (Vue.js)
`bash
npm run test
`

## Style Guide

### Commit Messages
- feat: Thêm tính năng mới
- fix: Sửa lỗi
- docs: Thay đổi documentation
- style: Format, thiếu dấu chấm phẩy,...
- refactor: Refactor code
- test: Thêm test cases
- chore: Cập nhật build tasks, package manager,...

### Code Style
- **JS/Vue:** Sử dụng 2 spaces cho indentation
- **PHP/Python:** Sử dụng 4 spaces cho indentation (Tuân thủ PSR-12 / PEP 8)
- Dòng không quá 80-120 ký tự tùy ngôn ngữ
- Đặt tên biến/hàm rõ ràng, có ý nghĩa bằng tiếng Anh
- Comment code khi cần thiết, đặc biệt với các logic AI phức tạp
