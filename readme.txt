README

---------------------------
T1 - Versionamento de dados
---------------------------

Repositório no github:
https://github.com/arbdias/MLOPS

Instalação do conda e criação do ambiente:
https://docs.conda.io/projects/miniconda/en/latest/ 

Comandos de criação do ambiente dentro do conda
  >conda create -n t1 python=3.9
  >conda activate t1

Clone do repositório github:
  >git clone https://github.com/arbdias/MLOPS.git

Criação do repositório DVC e commit:
  >pip install dvc
  >dvc init
  >git commit -m "DVC Init”

Baixar o código que o cliente disponibilizou e versionar. (Untitled-1.py)

Arquivo corrigido, renomeado e versionado via git:
  >git add t1/pet_care_model.py
  >git commit -m "PetCare Model first version”

Baixar os dados que o cliente disponibilizou e versionar. (ds.zip)

Copiar pasta descompacta (caminho t1/ds) e adicionar ao controle do DVC:
  >dvc add t1/ds

Commit da primeira versão do Dataset:
  >git add t1/.gitignore t1/ds.dvc
  >git commit -m "DataSet first version"

Atualiza o repositório no github:
  >git branch -M main
  >git push origin main (autenticar no browser)

A pasta t1/ds é versionada via DVC (e ignorada pelo git). Seu conteúdo é sincronizado em servidor de armazenamento remoto no GoogleDrive:
  >pip install dvc-gdrive
  >dvc remote add -d gdrive gdrive://16PThqzO2TLNJAtI6jUCaSe7_ke_FylPO
  >dvc push

Adicionando a config do GDrive ao repositório git
  >git add .dvc/config
  >git commit -m “Adding GDrive configuration for remote dataset storage”

Rodar o treinamento com os dados versionados
  >pip install tensorflow
  >pip install pillow
  >pip install scipy
  >python pet_care_model.py
