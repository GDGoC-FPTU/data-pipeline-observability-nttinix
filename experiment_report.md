# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** chưa cung cấp
**Name:** chưa cung cấp
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Tra loi on dinh, du lieu electronics hop le va de truy van. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Agent khong vo loi ky thuat, nhung bi du lieu ngoai le dan huong den ket luan sai va phi thuc te. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Garbage Data lam Agent that bai vi no khong con the tin vao cau truc va y nghia cua tung ban ghi. Dau tien, duplicate ID tao ra xung dot dinh danh, khien mot san pham co the bi nham voi san pham khac khi truy vet. Thu hai, gia tri `price` dang chu nhu `ten dollars` pha vo kieu du lieu so, dan den phep tim `idxmax()` bi loi va Agent dung han. Thu ba, outlier nhu `Nuclear Reactor` co gia qua lon lam sai lech logic lua chon "best product", vi Agent co the uu tien phan tu bat thuong thay vi san pham thuc te. Cuoi cung, null values va gia bang 0 lam giam do day du cua du lieu, de gay ra cac nhanh xu ly sai hoac ket luan thieu chinh xac. Noi cach khac, prompt co tot den dau van khong cuu duoc mot pipeline dau vao kem chat luong.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Dong y. Prompt tot giup Agent dien dat ro rang hon, nhung chat luong du lieu moi la nen tang de Agent suy luan dung. Khi du lieu sach, Agent tra loi nhanh va hop ly; khi du lieu rac, Agent co the tra loi sai hoac vo cung loi runtime. Vi vay, data quality va observability la buoc bat buoc truoc khi toi uu prompt.
