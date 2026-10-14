# 🧢 DropeLab — E-commerce de streetwear oversized

> **Vitrine do projeto.** O código-fonte é privado por ser um produto comercial.

🔗 **[Ver a loja (demo)](https://drope-lab.vercel.app)**

Sistema de vendas online completo para uma marca de **streetwear oversized**: loja virtual, painel administrativo e API, com **pagamento por cartão e Pix via Mercado Pago**. O desenvolvimento seguiu uma suíte de documentação técnica própria: requisitos (SRS), arquitetura, modelo de dados, referência da API (OpenAPI), plano de testes, implantação e segurança/LGPD.

![Node.js](https://img.shields.io/badge/Node.js_20-339933?style=flat&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL_16-4169E1?style=flat&logo=postgresql&logoColor=white)
![Sequelize](https://img.shields.io/badge/Sequelize-52B0E7?style=flat&logo=sequelize&logoColor=white)
![React](https://img.shields.io/badge/React_19-20232A?style=flat&logo=react&logoColor=61DAFB)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS_v4-06B6D4?style=flat&logo=tailwindcss&logoColor=white)
![Mercado Pago](https://img.shields.io/badge/Mercado_Pago-00B1EA?style=flat&logo=mercadopago&logoColor=white)
![Jest](https://img.shields.io/badge/Jest-C21325?style=flat&logo=jest&logoColor=white)
![Sentry](https://img.shields.io/badge/Sentry-362D59?style=flat&logo=sentry&logoColor=white)

## 🧩 Componentes

| Módulo | Descrição |
|---|---|
| **Loja** | React 19 + Vite + Tailwind v4: catálogo, carrinho, checkout, conta e pedidos |
| **Painel** | React: produtos, estoque, pedidos, cupons e dashboard, com perfis admin e operador |
| **API** | Node.js/Express + Sequelize + PostgreSQL, com 14 entidades e migrations versionadas |

## 💳 Pagamentos e estoque

- **Cartão:** tokenizado no navegador pelo SDK do Mercado Pago. O backend nunca recebe os dados do cartão
- **Pix:** QR Code e copia-e-cola gerados pelo Mercado Pago, com acompanhamento do status por polling
- **Webhook com assinatura HMAC validada** e status sempre reconfirmado na API do Mercado Pago (idempotente)
- **Estoque reservado atomicamente** na criação do pedido e liberado por job agendado quando a reserva expira

## 🛡️ Segurança e qualidade

- RBAC aplicado no backend (admin × operador), JWT e 2FA
- Helmet, rate limiting e validação de entrada (express-validator)
- Upload e otimização de imagens (Multer, Sharp, S3)
- Monitoramento de erros com Sentry e e-mails transacionais
- **Testes unitários e de integração** (Jest + PostgreSQL real) cobrindo cadastro, carrinho, checkout, reserva de estoque, cartão, Pix e webhook. Esses testes pegaram bugs reais antes de chegarem à produção.

---

Desenvolvido por **[Jolivan Abreu](https://github.com/JolivanAbreu)**.
