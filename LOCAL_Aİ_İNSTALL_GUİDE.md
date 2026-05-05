
# EduLoop Mobile AI Setup Markdown məzmunu
 📱 EduLoop: Mobil Local AI Quraşdırma Təlimatı

Bu sənəd **EduLoop** layihəsinin süni intellekt (AI) funksiyalarını birbaşa smartfon daxilində (server və internet bağlantısı olmadan) tamamilə yerli (local) olaraq necə işlətməli olduğunuzu izah edir. 

---

## 📋 Sistem Tələbləri

Mobil cihazlarda local AI modellərini işlətmək yüksək resurs tələb edir. Problemlərlə qarşılaşmamaq üçün minimum tələblər aşağıdakı kimidir:

* **Əməliyyat Sistemi:** Android 10+ 
* **Operativ Yaddaş (RAM):** Minimum 4GB (8GB və daha yuxarı tövsiyə olunur)
* **Boş Disk Sahəsi:** Modellərin ölçüsünə uyğun olaraq minimum 4GB - 8GB boş yer.

---

## 🧠 Mobil üçün Optimallaşdırılmış Modellər və Yükləmə Linkləri

Mobil cihazların prosessorları üçün xüsusi olaraq sıxılmış (Quantized - q4/q8) və kiçik parametli (2B-4B) modellər tövsiyə olunur:

| Model Adı | Ölçüsü | Tövsiyə Olunan Format | Yükləmə Linki | Təyinatı |
| :--- | :--- | :--- | :--- | :--- |
| **Google Gemma 2B** | ~1.4 GB | GGUF / MLC | [Hugging Face - Gemma 2B](https://huggingface.co/google/gemma-2b-it) | Sürətli sual-cavab və qeydlər |
| **Microsoft Phi-3 Mini** | ~2.2 GB | GGUF | [Hugging Face - Phi-3 Mini](https://huggingface.co/microsoft/Phi-3-mini-4k-instruct-gguf) | Mətn analizi və xülasələşdirmə |
| **Qwen 1.5 1.8B** | ~1.2 GB | GGUF | [Hugging Face - Qwen 1.5](https://huggingface.co/Qwen/Qwen1.5-1.8B-Chat-GGUF) | Zəif cihazlar üçün yüksək sürət |
