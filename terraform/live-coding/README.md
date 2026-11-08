# Workspace de Live Coding (Construção do Zero ao Fim)

Este é o **diretório de trabalho principal** durante as 8 horas do minicurso **"Redes.tf: da Teoria à Prática com Terraform e GCP"**!

Aqui, o facilitador (**Luan Sousa**) e os participantes **construirão os arquivos Terraform do início ao fim**, passo a passo, evoluindo desde a criação da primeira VPC até a conexão via **VPC Peering** com o Projeto Central e a organização em **Módulos**.

---

## Como Iniciar seu Workspace na Aula

```bash
# Entre nesta pasta
cd terraform/live-coding

# Ao longo da aula criaremos juntos:
# 1. versions.tf, providers.tf, variables.tf e terraform.tfvars (Etapa 00)
# 2. locals.tf, vpc.tf e outputs.tf                             (Etapa 01)
# 3. firewall.tf e compute.tf                                   (Etapa 02)
# 4. routes.tf e nat.tf                                         (Etapa 03)
# 5. peering.tf                                                 (Etapa 04)
```

> [!IMPORTANT]
> Use **exatamente** esses nomes de arquivo. Se você criar, por exemplo, `rede.tf` no lugar de `vpc.tf` e depois copiar um checkpoint, o mesmo recurso ficará declarado em dois arquivos e o Terraform acusará `Duplicate resource`. Para resolver, apague o arquivo com nome diferente.

---

## Ciclo de Cada Etapa

Você roda o Terraform **na sua própria máquina ou no seu Cloud Shell**, sempre dentro desta pasta. O `terraform.tfstate` gerado aqui é **só seu**: os colegas do mesmo projeto de grupo têm o state deles, e o sufixo `aluno-XX` + o CIDR `10.<ID>.0.0/24` garantem que os recursos não colidam.

**Uma única vez (Etapa 00):** depois de criar `versions.tf`, `providers.tf`, `variables.tf` e `terraform.tfvars`:

```bash
terraform init
```

**A cada etapa (01 a 04):**

```bash
terraform fmt && terraform validate
terraform plan     # o state é cumulativo: o plano mostra só o que a etapa acrescenta
terraform apply    # confirme com "yes"
```

**No final da aula:**

```bash
terraform destroy
```

> [!WARNING]
> **Não apague esta pasta nem troque de máquina no meio da aula.** Sem o `terraform.tfstate`, o Terraform perde o controle do que criou e os recursos ficam órfãos no projeto.
>
> **Cloud Shell:** normalmente já tem credenciais. Se você trocar de conta Google, rode de novo `gcloud auth application-default login`.

---

## Checkpoints (Caso perca algum passo)

Se você ficar para trás ou travar em algum erro, **não se preocupe**: durante a aula o facilitador vai liberar os **checkpoints** (gabaritos) de cada etapa, com as instruções de como sincronizar esta pasta com o ponto exato da turma **sem perder o seu `terraform.tfstate` nem o seu `terraform.tfvars`**.

> [!TIP]
> Por isso a importância de usar **exatamente** os nomes de arquivo listados acima: os checkpoints usam os mesmos nomes e os mesmos endereços de recurso, então dá para copiá-los por cima do seu código e seguir em frente.
