# FCAJ Internship Report

Báo cáo thực tập First Cloud AI Journey, dựng từ [fcj-workshop-template](https://github.com/thienluhoan/fcj-workshop-template)
theo [Quy định về Workshop](https://hcm-rules.awsfcaj.com/3-project/). Giữ nguyên theme/layout/workflow của template,
nội dung mẫu đã được thay bằng khung trống (rules cấm sao chép workshop mẫu).

Site: TODO (GitHub Pages)

## Cấu trúc (bắt buộc song ngữ: mỗi trang có `_index.md` = EN và `_index.vi.md` = VI)

| Mục | Thư mục | Ghi chú theo rules |
|---|---|---|
| Trang chủ | `content/_index*.md` | Thông tin sinh viên (2.1) + ảnh đại diện `static/images/avatar.png` |
| 1. Worklog | `content/1-Worklog/1.x-WeekX` | Week 1 → Week 12, công việc, kết quả, **References** (2.2) |
| 2. Proposal | `content/2-Proposal` | Bài toán, mục tiêu, kiến trúc sơ bộ, timeline, **Cost**, rủi ro (2.3) |
| 3. Blogs | `content/3-BlogsPosted/3.1..3.3` | ≥ 3 blog đã đăng AWS Study Group (2.4) |
| 4. Events | `content/4-EventParticipated/4.1..4.3` | ≥ 3 sự kiện, **ảnh check-in rõ mặt** (2.5) |
| 5. Workshop | `content/5-Workshop/5.1..5.9` | Overview, Prerequisite, Architecture, Step-by-step, Testing, Cost, Demo, Clean-up, Troubleshooting (2.6, 3.2, 4.x) |
| 6. Tự đánh giá | `content/6-Self-evaluation` | 8 tiêu chí, Tốt/Khá/Trung bình + nhận xét (2.7) |
| 7. Feedback | `content/7-Feedback` | Cảm nhận, mức hài lòng, cải thiện, có giới thiệu bạn bè không (2.8) |

Còn bao nhiêu chỗ chưa điền: `git grep -c "TODO" -- content`

## Ảnh chụp màn hình - quy ước

- Đặt ở `static/images/<mục>/<mục con>/NN-mo-ta.png`, ví dụ `static/images/5-Workshop/5.4-Deployment/5.4.1/01-create-vpc.png`.
- Chèn vào trang bằng đường dẫn bắt đầu từ `/images/...`: `![Create VPC](/images/5-Workshop/5.4-Deployment/5.4.1/01-create-vpc.png)`
  (render hook tự thêm sub-path của GitHub Pages).
- Tên file: tiếng Anh, chữ thường, gạch ngang, đánh số theo thứ tự thao tác.
- Chụp đúng vùng liên quan (không cả màn hình), khoanh đỏ chỗ cần bấm/giá trị cần nhập, rộng khoảng 1200-1600 px.
- **Che/cắt thông tin nhạy cảm** trước khi commit: Account ID, ARN có account ID, access key, email, số điện thoại, IP public.
- Mỗi ảnh có chú thích (alt text) mô tả nội dung; trang VI dùng lại cùng ảnh.

## File đính kèm

`static/attachments/` - `architecture.xml` (draw.io do bạn tự vẽ), template CloudFormation/Terraform, script, PDF dự toán chi phí.
Link trong bài: `[architecture.xml](/attachments/architecture.xml)`.

## Xem thử trên máy

```powershell
..\tools\hugo\hugo.exe server        # mở http://localhost:1313/<tên-repo>/
```

## Deploy

Push lên nhánh `main` → GitHub Actions (`.github/workflows/hugo.yml`, Hugo 0.134.3) build và đẩy sang nhánh `gh-pages`
→ GitHub Pages phục vụ từ nhánh `gh-pages`. `baseURL` trong `config.toml` phải khớp URL Pages.

## Thay đổi so với template

- `layouts/_default/_markup/render-image.html`, `render-link.html`: đường dẫn `/images/...`, `/attachments/...` chạy đúng dưới
  `https://<user>.github.io/<repo>/`; link ngoài mở tab mới.
- `layouts/partials/logo.html`: logo trỏ về trang chủ đúng ngôn ngữ và sub-path.
- Link nội bộ viết chữ thường (GitHub Pages phân biệt hoa/thường).
- Thêm Event 3 (rules yêu cầu ≥ 3 sự kiện), mục Workshop theo đúng danh sách bắt buộc, tự đánh giá theo 8 tiêu chí của rules.
- Bỏ `.gitmodules` (theme đã được vendor sẵn trong repo template).
