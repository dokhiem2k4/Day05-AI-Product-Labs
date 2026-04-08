# AI Product Canvas - VinMec MyVinMec tai kham thong minh

Canvas dien cho bai toan AI agent tro ly suc khoe giup benh nhan VinMec, dac biet la nguoi cao tuoi, khong bo lo lich tai kham.

---

## Canvas

|   | Value | Trust | Feasibility |
|---|-------|-------|-------------|
| **Cau hoi guide** | User nao? Pain gi? AI giai quyet gi ma cach hien tai khong giai duoc? | Khi AI sai thi user bi anh huong the nao? User biet AI sai bang cach nao? User sua bang cach nao? | Cost bao nhieu/request? Latency bao lau? Risk chinh la gi? |
| **Tra loi** | User chinh la benh nhan da kham/xuat vien can tai kham dung han, dac biet nguoi cao tuoi va nguoi cham soc. Pain hien tai: de quen moc tai kham, kho thao tac tren app MyVinMec, kho canh slot phu hop, phai goi tong dai hoac nho nguoi than dat ho. AI agent giai quyet bang cach doc moc tai kham tu chi dinh sau kham, chu dong nhac dung thoi diem, kiem tra slot trong khoang khuyen nghi, de xuat lich phu hop, ho tro dat lich nhanh va nhac nho da kenh (app, SMS, Zalo, voice call) theo thoi quen tung benh nhan. | Neu AI nhac sai thoi diem, sai co so, sai chuyen khoa hoac dat sai slot, benh nhan co the lo cham soc lien tuc hoac mat cong di lai. User biet AI co the sai nho man hinh xac nhan hien ro: bac si/chuyen khoa, ngay gio, co so, ly do duoc goi y va moc tai kham theo chi dinh. User sua bang cach doi lich de xuat, chon lai co so, chuyen cho nguoi cham soc phe duyet, hoac bam ket noi tong dai/nhan vien. Voi user lon tuoi, can co fallback ro rang: xac nhan bang 1 cham, nhac lai qua cuoc goi, va luon co lua chon gap nguoi that. | Cost [?] uoc tinh ~0.01-0.05 USD/luot orchestration gom phan tich chi dinh, check slot va gui nhac; latency muc tieu: de xuat lich <5s, dat lich <10s neu API lich hen on dinh. Risk chinh: doc sai chi dinh tai kham, du lieu slot khong realtime, loi dong bo voi he thong dat lich, thong bao da kenh khong den, va rui ro quyen rieng du lieu y te. Can uu tien rule + workflow cho booking, chi dung LLM o khau tom tat/giai thich/ca nhan hoa. |

---

## Automation hay augmentation?

☐ Automation - AI lam thay, user khong can thiep
☑ Augmentation - AI goi y, user quyet dinh cuoi cung

**Justify:** Day la bai toan y te co rui ro trust cao, nen V1 nen la augmentation co "bounded automation". AI co the tu dong lam cac tac vu low-risk nhu theo doi moc tai kham, check slot, nhac da kenh va pre-fill booking. Buoc chot lich cuoi cung nen do benh nhan/nguoi cham soc xac nhan; chi nen cho phep auto-book khi user da uy quyen ro rang truoc do cho mot bac si/co so/khoang gio cu the.

---

## Learning signal

| # | Cau hoi | Tra loi |
|---|---------|---------|
| 1 | User correction di vao dau? | Moi lan user doi ngay gio, doi co so, doi kenh nhac, tu choi lich AI de xuat, hoac chuyen sang tong dai deu tro thanh correction signal cho he thong goi y lich va kenh nhac. |
| 2 | Product thu signal gi de biet tot len hay te di? | Ty le dat lich tai kham thanh cong, ty le den kham dung hen, ty le bo lo lich, ty le user chap nhan lich AI de xuat, so lan phai doi lich/nhan ho tro nguoi that, open/click/acknowledge reminder, va ly do bo qua reminder. |
| 3 | Data thuoc loai nao? ☐ User-specific · ☐ Domain-specific · ☐ Real-time · ☐ Human-judgment · ☐ Khac: ___ | User-specific, Domain-specific, Real-time, Human-judgment. Day la du lieu hanh vi va van hanh rat dac thu cua VinMec: moc tai kham theo benh ly, slot thuc te, so thich kenh nhac, va correction cua benh nhan/nguoi cham soc. |

**Co marginal value khong?** Co. Model co the da "biet" cach nhac lich noi chung, nhung khong biet duoc moc tai kham thuc te cua tung benh nhan, slot cua tung co so VinMec, kenh nao nguoi cao tuoi phan hoi tot hon, va khi nao can escalte sang nguoi cham soc. Day la first-party data kho bi copy va co the tao flywheel ro rang: nhac dung hon -> den kham dung hen hon -> co them data correction/response -> goi y va nhac tiep tuc ca nhan hoa hon.

---

## Ghi chu gia thuyet

1. Gia dinh MyVinMec co the truy cap duoc chi dinh tai kham, lich hen va trang thai slot qua API noi bo.
2. Gia dinh user dong y nhan nhac nho da kenh va co the chi dinh nguoi cham soc dong hanh.
3. Neu chua tin du vao booking agent, co the ship V1 theo lo trinh: nhac lich thong minh -> check slot + de xuat -> booking co xac nhan -> auto-book cho user da uy quyen.
