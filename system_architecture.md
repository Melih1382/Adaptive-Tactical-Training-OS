# 🏗️ System Architecture & Workflow Specifications

## 1. Multi-Agent Orchestration (Backend)
* **Orchestrator Agent:** Gelen kullanıcı profili ve RAG veritabanı analizlerini toplar.
* **Pedagogy/Tactical Agent:** Personelin stres seviyesine ve hata oranına göre senaryo zorluğunu (Aralıklı Tekrar algoritması ile) anlık olarak günceller.
* **UI Generator Agent:** Taktik senaryoyu, istemcinin (Client) anlayacağı Server-Driven UI JSON paketlerine dönüştürür.
* **Framework:** LangChain / AutoGen tabanlı Python asenkron mimarisi.

## 2. Server-Driven UI (Frontend)
* **Teknoloji:** React / Next.js (Statik sayfa barındırmaz).
* **İşleyiş:** Backend'den gelen JSON yapısını (`{"role": "uav_operator", "scenario": "engine_failure", "ui_type": "hud_simulation"}`) dinler ve ekran bileşenlerini milisaniyeler içinde Framer Motion animasyonları ile yeniden inşa eder.

## 3. Data Privacy & Air-Gapped Compatibility
* Sistem, bulut bağımlılığı gerektirmez. Kendi kapalı ağında (On-Premise) barındırılan yerel LLM (Örn: Llama 3) modelleri ve ChromaDB/Milvus vektör veritabanları ile RAG işlemlerini dış dünyaya tamamen kapalı bir şekilde yürütür.