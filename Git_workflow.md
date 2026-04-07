### Branches

#### main/master (Release version)

- Chứa code version hiện tại được release trên store.
- Member sẽ không được thao tác bất kỳ tác vụ nào trên branch này.
- Mỗi lần app được published lên store, Manager sẽ merge code từ `develop` vào branch này và gắn tag version released.

#### develop

- Chứa code version đang được phát triển.
- Member chỉ được tạo PR vào branch này sau mỗi lần hoàn thành task (không được push code trực tiếp).
- Reviewer có trách nhiệm review PR.
- Manager có trách nhiệm review PR và merge code vào `develop`.

#### feat/\*

- Branch chức năng theo task trên Larksuite.
- Member đặt tên branch theo **Style list**.
- Sau khi hoàn thành task, tạo PR vào `develop` (không được merge trực tiếp).

#### Style list

| Name       | Description                               |
| ---------- | ----------------------------------------- |
| `doc`    | Thêm mới, chỉnh sửa documents, README |
| `feat`   | Thêm tính năng mới                    |
| `fix`    | Fix một hoặc nhiều bug                 |
| `revert` | Revert một commit gần nhất             |

#### Ví dụ đặt tên branch

| Task                    | Good                    | Bad                                          |
| ----------------------- | ----------------------- | -------------------------------------------- |
| Viết README cho repo   | `docs/add_readme`     | `readme`, `add_readme`                   |
| Sửa đổi UI           | `feat/new_ui`         | `developer_new_ui`, `feature/new_ui`     |
| Fix bug màn hình Home | `fix/bug_home_screen` | `fix_bug_home_screen`, `fix/home_screen` |

### Commit rules

```bash
# Tạo commit
git commit -m "type(scope): Reference message"
# Ví dụ:
git commit -m "feat(login): Create UI login"

# Thêm thay đổi vào commit cuối cùng:
git commit --amend
# hoặc
git commit --amend -m "type(scope): Reference message"

# Đẩy lên remote sau amend:
git push -f
```

> Ai chưa hiểu `--amend` có thể hỏi để được giải thích thêm.

### Git Flow

1. Trước khi bắt đầu task, pull lại branch `develop`.
2. Tạo branch feature từ `develop` theo [Style list](#style-list).
3. Hoàn thành công việc, tạo PR merge vào `develop` (gắn reviewer là người review, assignee cho bản thân).
4. Mọi reviewer có thể review chéo. Gắn label cho PR nếu cần thay đổi.
5. Nếu có `requested changes`, member fix theo note, rồi nhấn `Resolve conversation` và remove label để reviewer review lại.
6. Khi PR approved và merge vào `develop`, member build APK/IPA và tạo task cho tester trên Larksuite.

> Trường hợp task chưa có git hoặc chưa có branch `develop`, báo với Manager.

> Trường hợp chỉnh sửa PR theo review, sau khi chỉnh sửa xong, member nhớ remove label để reviewer biết PR đã sẵn sàng review lại.

> #LƯU Ý: Cần bật thông báo kênh `📣┇github-report` để nhận thông báo khi có thay đổi.

### Chú ý

- Với task update chức năng nhỏ hoặc fix bug mà chỉ có một member thực hiện: chỉ push đúng một commit.
- Nếu cần thay đổi sau commit, dùng `--amend`.

### Base project

- Tất cả dự án sử dụng chung một base.
- Khi bắt đầu project mới, Manager tạo repo và push lên branch `master`.
- Member tạo branch feature từ `develop` để làm việc.
- Member có thể đề xuất thay đổi base project qua PR.
- Manager review và approve nếu thay đổi hữu ích.

### Label names

| Name          | Description                                                                                                         |
| ------------- | ------------------------------------------------------------------------------------------------------------------- |
| `conflict`  | PR bị conflict với nhánh chính                                                                                  |
| `invalid`   | PR làm không đúng hoặc thiếu chức năng theo mô tả task trên Lark                                         |
| `in review` | PR đang được review                                                                                             |
| `approved`  | PR được chấp nhận, sẵn sàng merge. Reviewer gắn label này khi approval; Manager review nhanh trước merge |
| `hold`      | Chỉ Manager được gắn; task bị hủy bỏ và PR giữ lại không merge                                          |

> Nếu repo chưa có những label này, reviewer có thể thêm, nhớ xóa label không nằm trong danh sách.

> Khi sửa hoặc thêm label, set màu đúng:

- `approved`: #0e8a16
- `bug`: #d73a4a
- `conflict`: #E99695
- `hold`: #FEF2C0
- `in review`: #77F550
- `invalid`: #FBCA04

### Roles

#### Reviewer

- Review code để nâng cao kỹ năng.
- Được phép review chéo.
- Reviewer trước khi review set label `in review`, remove khi xong.
- Nếu chấp nhận PR, gắn label `approved`. Nếu không, gắn `invalid`.

#### Manager

- Tạo repo.
- Review task.
- Merge task (squash merge) và xóa branch feature sau merge.
