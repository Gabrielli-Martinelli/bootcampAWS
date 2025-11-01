# Orquestração com AWS Step Functions 🎛️

AWS Step Functions é um serviço de orquestração de workflows que permite **combinar serviços AWS e funções** (por exemplo, Lambdas, ECS tasks, APIs) em fluxos resilientes, observáveis e fáceis de manter.  
- como o maestro de uma orquestra que garante que cada instrumento (serviço) toque na hora certa, repetindo, desviando ou tratando erros quando necessário.


---

## Conceitos principais 🧱

| Conceito | O que é | 
|----------|---------|
| **State Machine** | Definição do workflow (lista de estados + transições) | 
| **State** | Um passo do workflow (Task, Choice, Wait, Parallel, Map, Succeed, Fail, Pass) | 
| **Task** | Estado que executa trabalho (ex: invocar Lambda, ECS, Step Functions API) | 
| **Choice** | Ramificação condicional (if/else) | 
| **Parallel** | Executa ramos em paralelo | 
| **Map** | Executa um sub-workflow para cada item de uma lista | 
| **Wait** | Pausa o workflow por um tempo ou até uma data | 
| **Retry / Catch** | Políticas de reexecução e tratamento de erro | 
| **Amazon States Language (ASL)** | JSON que descreve a state machine | 
---

## Tipos de estados (rápido resumo)

| Estado | Uso comum | Quando usar |
|--------|-----------|-------------|
| **Task** | Executar trabalho (Lambda, ECS, Activity) | Chamar uma função ou serviço |
| **Choice** | Tomar decisões | Rotas de sucesso/erro baseadas em dados |
| **Parallel** | Rodar ramos simultâneos | Processos independentes que podem ocorrer ao mesmo tempo |
| **Map** | Iterar sobre arrays | Processar listas (ex: lote de arquivos) |
| **Wait** | Aguardar | Atrasos, polling ou workflow baseado em tempo |
| **Pass** | Passar dados (sem trabalho) | Transformações simples durante debugging |
| **Succeed / Fail** | Encerrar com sucesso ou falha | Finalizar a máquina |
| **Retry / Catch** | Re-tentativas e captura de erros | Tornar o workflow resiliente |

---

## Workflow (passo-a-passo) — visão prática 🧭

1. **Definir objetivo** — qual tarefa a máquina precisa orquestrar? (ex: processar pedidos, pipeline ETL, pipeline de ML)  
2. **Mapear etapas** — listar todas as etapas, entradas/saídas e possíveis falhas.  
3. **Escolher estados** — para cada etapa, decida se é `Task`, `Choice`, `Parallel`, `Map`, etc.  
4. **Desenhar fluxos de dados** — quais dados cada passo recebe e devolve (use `InputPath`, `Parameters`, `ResultPath`, `OutputPath`).  
5. **Configurar retry/catch** — defina políticas de retry e handling de erros para `Task` críticos.  
6. **Testar localmente** — simule execuções (Step Functions Local, SAM CLI) e ajuste.  
7. **Deploy e observabilidade** — publicar, ativar logs (CloudWatch), e instrumentar (X-Ray/Logging).  
8. **Monitorar e iterar** — checar execuções, ajustar timeouts/retries/limites.

---

## Prática simples (workflow)
// observação: aparece um (X) no design nos estados que chamam uma função lambda pois não coloquei as infos das regions para não implementar de fato o workflow, fiz apenas para prática e teste! 

Workflow: RecebeArquivo → se válido, processarArquivo (Lambda) → notificar → sucesso. Se inválido → erro.

<img width="701" height="519" alt="workflow" src="https://github.com/user-attachments/assets/7290a182-51b7-4e67-81a4-0dba888297a9" />
