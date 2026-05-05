import os

# EduLoop Mobile AI Setup Markdown məzmunu
md_content = """# 📱 EduLoop: Mobil Local AI Quraşdırma Təlimatı

Bu sənəd **EduLoop** layihəsinin süni intellekt (AI) funksiyalarını birbaşa smartfon daxilində (server və internet bağlantısı olmadan) tamamilə yerli (local) olaraq necə işlətməli olduğunuzu izah edir. Bu faylı GitHub repozitoriyanıza `MOBILE_AI_SETUP.md` adı ilə əlavə edə bilərsiniz.

---

## 📋 Sistem Tələbləri

Mobil cihazlarda local AI modellərini işlətmək yüksək resurs tələb edir. Problemlərlə qarşılaşmamaq üçün minimum tələblər aşağıdakı kimidir:

* **Əməliyyat Sistemi:** Android 10+ (64-bit) və ya iOS 14+
* **Operativ Yaddaş (RAM):** Minimum 6GB (8GB və daha yuxarı tövsiyə olunur)
* **Boş Disk Sahəsi:** Modellərin ölçüsünə uyğun olaraq minimum 4GB - 8GB boş yer.

---

## 🛠 1. Lazım olan Mobil Tətbiqlər (İnterfeyslər)

Telefon daxilində `.gguf` və ya `MLC` formatlı modelləri işlətmək üçün aşağıdakı tətbiqlərdən birini yükləməlisiniz:

### 🤖 Android üçün:
1.  **Layla / Layla Lite:** Çox sadə interfeysə malikdir və local modelləri birbaşa dəstəkləyir. [Google Play Linki](https://play.google.com/store/apps/details?id=com.shareit.layla)
2.  **MLC LLM:** Açıq mənbəli, yüksək performanslı iş mühiti. [MLC Android Quraşdırma Sənədi](https://mlc.ai/mlc-llm/docs/install/android.html)
3.  **Chatter UI:** Yerli olaraq `.gguf` modellərini işlətmək üçün mükəmməl açıq mənbəli proqram. [GitHub Repozitoriyası](https://github.com/mtopolnik/ChatterUI)

### 🍏 iOS (iPhone / iPad) üçün:
1.  **MLC LLM:** iOS cihazları üçün optimallaşdırılmış versiya. [MLC iOS Quraşdırma Sənədi](https://mlc.ai/mlc-llm/docs/install/ios.html)
2.  **Private LLM:** Tamamilə oflayn işləyən və məlumat gizliliyini qoruyan pullu/pulsuz alternativ. [App Store Linki](https://apps.apple.com/us/app/private-llm/id6448106861)

---

## 🧠 2. Mobil üçün Optimallaşdırılmış Modellər və Yükləmə Linkləri

Mobil cihazların prosessorları üçün xüsusi olaraq sıxılmış (Quantized - q4/q8) və kiçik parametli (2B-4B) modellər tövsiyə olunur:

| Model Adı | Ölçüsü | Tövsiyə Olunan Format | Yükləmə Linki | Təyinatı |
| :--- | :--- | :--- | :--- | :--- |
| **Google Gemma 2B** | ~1.4 GB | GGUF / MLC | [Hugging Face - Gemma 2B](https://huggingface.co/google/gemma-2b-it) | Sürətli sual-cavab və qeydlər |
| **Microsoft Phi-3 Mini** | ~2.2 GB | GGUF | [Hugging Face - Phi-3 Mini](https://huggingface.co/microsoft/Phi-3-mini-4k-instruct-gguf) | Mətn analizi və xülasələşdirmə |
| **Qwen 1.5 1.8B** | ~1.2 GB | GGUF | [Hugging Face - Qwen 1.5](https://huggingface.co/Qwen/Qwen1.5-1.8B-Chat-GGUF) | Zəif cihazlar üçün yüksək sürət |

---

## 💻 3. İnkişaf etdiricilər üçün: Termux ilə Quraşdırma (Android Advanced)

Əgər EduLoop mobil tətbiqini CLI (Terminal) üzərindən yerli olaraq test etmək istəyirsinizsə, Android-də **Termux** istifadə edə bilərsiniz:

1.  [F-Droid](https://f-droid.org/) platformasından **Termux** yükləyin (Google Play versiyası köhnəlib).
2.  Termux terminalını açın və aşağıdakı əmrlərlə mühiti qurun:
    ```
```text?code_stdout&code_event_index=1
Fayl uğurla yaradıldı: MOBILE_AI_SETUP.md

```bash
    pkg update && pkg upgrade -y
    pkg install python python-pip git clang make -y
    pip install huggingface_hub
    ```
3.  Hugging Face-dən istədiyiniz modeli skriptlə endirin:
    ```bash
    huggingface-cli download microsoft/Phi-3-mini-4k-instruct-gguf Phi-3-mini-4k-instruct-q4.gguf --local-dir . --local-dir-use-symlinks False
    ```

---

## ⚙️ 4. EduLoop Mobil Konfiqurasiyası

EduLoop mobil tətbiq kodunun uzaq server əvəzinə daxili local AI mühitinə (məsələn, MLC local host portuna və ya Chatter UI API-na) bağlanması üçün layihə daxilindəki `.env.production` və ya konfiqurasiya faylını belə tənzimləyin:

```env
# Mobil yerli qoşulma tənzimləmələri
MOBILE_AI_PROVIDER=local_mlc
MOBILE_AI_API_URL=[http://127.0.0.1:8080/v1](http://127.0.0.1:8080/v1)
MOBILE_DEFAULT_MODEL=gemma-2b
OFFLINE_MODE_ENABLED=true
