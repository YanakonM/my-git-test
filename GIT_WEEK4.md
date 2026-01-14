# Week 4: Git Flow & Release Management 🚀
**วันที่**: 14 มกราคม 2026  
**ระดับ**: Advanced  
**ใช้เวลา**: 1-2 ชั่วโมง
---
## 🎯 เป้าหมายของสัปดาห์นี้
1. เรียนรู้ **Git Flow** - โครงสร้างการทำงานแบบมืออาชีพ
2. เข้าใจ **Version Tagging** - การติดป้ายเวอร์ชัน
3. ฝึก **Release Management** - การจัดการ Release อย่างเป็นทางการ
---
## 📚 ทฤษฎี: Git Flow คืออะไร?
**Git Flow** เป็นโมเดลการจัดการ Branch ที่ออกแบบโดย Vincent Driessen เป็นมาตรฐานที่ทีมพัฒนาซอฟต์แวร์ใช้กันทั่วโลก
### โครงสร้าง Branch
main (Production) ↑ develop (Development) ↑ feature/* (Features)

#### 1. main Branch
- โค้ดที่พร้อม Production (เว็บจริง)
- ไม่แก้โค้ดตรงนี้โดยตรง
- รับ merge จาก develop เท่านั้น
#### 2. develop Branch
- ที่รวมโค้ดของทีมพัฒนา
- รับ merge จาก feature branches
- เมื่อพร้อมแล้ว ส่งไป main
#### 3. feature/* Branches
- Branch สำหรับทำงานแต่ละชิ้น
- ตั้งชื่อ: feature/ชื่องาน (เช่น feature/login, feature/payment)
- สร้างจาก develop, merge กลับเข้า develop
---
## 🛠️ ขั้นตอนการทำงาน
### Phase 1: ตั้งค่า Git Flow
#### 1.1 สร้าง develop branch
\`\`\`bash
# อยู่ที่ main
git checkout main
git pull origin main
# สร้าง develop
git checkout -b develop
git push -u origin develop
\`\`\`
#### 1.2 สร้าง feature branch
\`\`\`bash
# อยู่ที่ develop
git checkout develop
# สร้าง feature
git checkout -b feature/advanced-profile
\`\`\`
#### 1.3 ทำงานใน feature
สร้างไฟล์ `advanced-profile.md`:
\`\`\`bash
# สร้างไฟล์และเพิ่มเนื้อหา
# (ดูตัวอย่างด้านล่าง)
# Commit
git add advanced-profile.md
git commit -m "feat: add advanced profile"
git push -u origin feature/advanced-profile
\`\`\`
#### 1.4 Merge feature → develop
\`\`\`bash
git checkout develop
git merge feature/advanced-profile
git push origin develop
\`\`\`
#### 1.5 Release: develop → main
\`\`\`bash
git checkout main
git merge develop
git push origin main
\`\`\`
---
### Phase 2: Version Tagging
#### 2.1 สร้าง Tag
\`\`\`bash
git checkout main
git tag -a v1.0.0 -m "Release version 1.0.0"
\`\`\`
**รูปแบบ Semantic Versioning**:
- v**Major**.**Minor**.**Patch**
- v1.0.0 = เวอร์ชันใหญ่แรก
- v1.1.0 = เพิ่มฟีเจอร์ใหม่
- v1.0.1 = แก้บัค
#### 2.2 Push Tags
\`\`\`bash
# Push tag เดียว
git push origin v1.0.0
# หรือ push ทั้งหมด
git push origin --tags
\`\`\`
#### 2.3 ดู Tags
\`\`\`bash
# ดู tags ทั้งหมด
git tag
# ดูรายละเอียด tag
git show v1.0.0
\`\`\`
---
### Phase 3: Release Management
#### 3.1 สร้าง CHANGELOG.md
ไฟล์นี้บันทึกการเปลี่ยนแปลงทุกเวอร์ชัน:
\`\`\`markdown
# Changelog
## [1.0.0] - 2026-01-14
### Added
- Git Flow implementation
- Advanced profile system
- Version tagging
### Changed
- Upgraded to advanced workflow
\`\`\`
#### 3.2 สร้าง Release บน GitHub
1. ไปที่ Repository → **Releases**
2. คลิก **Create a new release**
3. เลือก Tag: v1.0.0
4. ใส่ Title: "Version 1.0.0 - Git Flow"
5. ใส่ Release Notes (ดูตัวอย่างใน implementation plan)
6. **Publish release**
---
## 📌 คำสั่งสำคัญที่ต้องจำ
| คำสั่ง | ความหมาย |
|--------|----------|
| `git checkout -b develop` | สร้าง develop branch |
| `git checkout -b feature/xxx` | สร้าง feature branch |
| `git merge <branch>` | รวม branch เข้ามา |
| `git tag -a v1.0.0 -m "msg"` | สร้าง annotated tag |
| `git push origin --tags` | Push tags ทั้งหมด |
| `git tag` | ดู tags ทั้งหมด |
---
## ✅ Checklist
- [ ] สร้าง develop branch จาก main
- [ ] สร้าง feature branch จาก develop
- [ ] ทำงานใน feature และ commit
- [ ] Merge feature → develop
- [ ] Merge develop → main (Release)
- [ ] สร้าง Tag v1.0.0
- [ ] Push tags ขึ้น GitHub
- [ ] สร้าง CHANGELOG.md
- [ ] สร้าง Release บน GitHub พร้อม Notes
- [ ] อ่านเอกสารนี้อีกครั้งเพื่อทบทวน
---
## 🎓 สิ่งที่เรียนรู้
### ได้อะไร?
- ✅ เข้าใจ Git Flow และทำได้
- ✅ รู้จักการติด Tag เวอร์ชัน
- ✅ สร้าง Release อย่างเป็นทางการ
- ✅ เขียน Changelog บันทึกการเปลี่ยนแปลง
### ทำไมต้องใช้?
- **Git Flow** = ทีมไม่สับสน ทุกคนรู้ว่า branch ไหนทำอะไร
- **Tags** = อ้างอิงเวอร์ชันได้ชัดเจน ย้อนกลับได้ง่าย
- **Releases** = User รู้ว่า version นี้เปลี่ยนอะไรบ้าง
### ใช้ตอนไหน?
- **Git Flow**: โปรเจคที่มีทีม หรือ release แบบมี cycle
- **Tags**: ทุกครั้งที่ release เวอร์ชันใหม่
- **Releases**: เมื่อต้องการให้ User download หรืออ่าน release notes
---
## 🚀 Next Steps
**Week 5: CI/CD & Automation**
- เชื่อม GitHub กับ Vercel/GitHub Pages
- ตั้งค่า Auto-deployment
- เรียนรู้ GitHub Actions
**Stay tuned!** 🎉
---
## 📖 เอกสารอ้างอิง
- [Git Flow Original Post](https://nvie.com/posts/a-successful-git-branching-model/)
- [Semantic Versioning](https://semver.org/)
- [Keep a Changelog](https://keepachangelog.com/)
- [GitHub Releases Guide](https://docs.github.com/en/repositories/releasing-projects-on-github)
---
**สร้างโดย**: Yanakorn M.  
**วันที่**: 14 มกราคม 2026  
**สถานะ**: Week 4 Completed ✅