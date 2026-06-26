# Cloudflare secure deployment guide for CCCD Tool

## Muc tieu

Chuyen CCCD Tool tu GitHub Pages public sang Cloudflare Pages co Cloudflare Access dang nhap de phu hop van hanh noi bo.

## Trang hien co

- `/cccd-tabs/`: workspace 2 tab.
- `/bm01a-cccd/`: nhap va quet tung CCCD, xuat PDF BM01A.
- `/bm01a-cccd-bulk/`: doc QR hang loat tu nhieu anh, xuat Excel `.xlsx`.
- `/bm01a-cccd-qr/`: ban QR Boost.

## Nguyen tac bao mat

- Khong upload anh CCCD len server.
- Khong luu anh CCCD tren GitHub, Cloudflare Pages hoac Supabase.
- Xu ly QR, Excel, PDF ngay tren trinh duyet nguoi dung.
- Bao ve toan bo domain bang Cloudflare Access.
- Repo nen de private sau khi chuyen sang Cloudflare.

## Thiet lap Cloudflare Pages

1. Cloudflare Dashboard -> Workers & Pages -> Create application -> Pages -> Connect to Git.
2. Chon repository `anhvt777/cccd-tool`.
3. Production branch: `cloudflare-secure`.
4. Framework preset: None / Static HTML.
5. Build command: de trong hoac `exit 0`.
6. Build output directory: `/`.
7. Save and Deploy.

## Thiet lap Cloudflare Access dang nhap

1. Zero Trust -> Access controls -> Applications.
2. Create new application.
3. Chon Self-hosted.
4. Gan domain cua Pages hoac custom domain, vi du `cccd-tool.<domain>`.
5. Tao policy Allow chi gom email duoc phep su dung.
6. Khong dung Include Everyone.
7. Khong dung Include Login Methods = One-time PIN don le, vi nhu vay moi email hop le deu co the vao.
8. Dat session duration ngan, khuyen nghi 8-12 gio.
9. Bat MFA neu co dieu kien.

## Cau hinh GitHub repo sau khi chuyen

- Chuyen repo sang Private.
- GitHub Pages co the tat neu khong con dung link public.
- Chi cap Cloudflare GitHub App quyen vao repo nay, khong cap toan bo tai khoan neu khong can.

## Kiem thu truoc khi dung chinh thuc

- Mo domain Cloudflare bang trinh duyet an danh: phai hien man hinh dang nhap Cloudflare Access.
- Email khong nam trong allow list: khong vao duoc.
- Email duoc phep: vao duoc workspace 2 tab.
- Test camera tren iPhone.
- Test doc QR hang loat 10-20 anh.
- Test xuat Excel `.xlsx`.
- Test xuat PDF BM01A.
- Kiem tra lai DevTools/Network: khong co request upload anh CCCD len server.

## Huong van hanh khuyen nghi

- Link noi bo su dung: Cloudflare Access protected domain.
- Anh CCCD luu rieng tren thiet bi hoac thu muc noi bo, khong luu trong web.
- Excel xuat ra can luu vao thu muc noi bo theo ngay.
- Sau khi hoan tat, xoa cache/local data tren may dung chung.
