Thực hành Git
==============

Bài 1-2
-------
Các commit đầu tiên lần lượt là Initial commit: add html and css, Update html content, Add javascript file, và Update style and notes. Ở commit đầu, notes.txt được để untracked; sau đó nó được thêm ở commit cuối của Bài 2.

Bài 3: reset
------------
| Lệnh | Working Directory | Staging Area | Repository |
|---|---|---|---|
| reset --soft HEAD~1 | Giữ nguyên file | Giữ thay đổi ở trạng thái staged | Bỏ commit cuối khỏi nhánh |
| reset --mixed HEAD~1 | Giữ nguyên file | Bỏ staging; file mới thành untracked | Bỏ commit cuối khỏi nhánh |
| reset --hard HEAD~1 | Khôi phục/xóa file tracked theo commit đích | Khớp với commit đích | Bỏ commit cuối khỏi nhánh |

Ghi chú: reset --hard không tự xóa file untracked vốn đã tồn tại trước đó. Trong demo, temp.txt được tạo và commit; vì vậy hard reset quay về trước commit tạo file và xóa file đó khỏi working tree.

Bài 4-5
-------
Remote origin được cấu hình từ URL được giao. Khi push thành công, `git push -u origin main` thiết lập upstream. `git pull` thực chất thực hiện fetch rồi tích hợp thay đổi bằng merge (hoặc rebase nếu cấu hình pull.rebase bật).

Bài 6
-----
Thư mục personal-intro chứa trang cá nhân. Lịch sử có các commit Initial structure, Add introduction section, Style introduction section, một commit CSS sai, và commit revert tự động tạo để hoàn tác lỗi mà vẫn giữ các commit hợp lệ.

Câu hỏi staging area
--------------------
Staging area cho phép chọn chính xác phần thay đổi sẽ nằm trong commit kế tiếp. Không có nó, các thay đổi đang dở dang hoặc không liên quan sẽ dễ bị gộp chung; khó tạo commit nhỏ, rõ mục đích và review được.

Câu hỏi reset sau push
----------------------
Reset --hard sau khi push có thể làm lịch sử trên remote khác với lịch sử local; nếu force-push, commit mà đồng đội đã dựa vào có thể biến mất khỏi nhánh chung. Nên dùng revert trên nhánh đã chia sẻ, hoặc phối hợp rõ ràng trước khi viết lại lịch sử.
