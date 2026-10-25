# Como transformar uma TV Box Android em um computador com Linux (Armbian)

## Descobrindo qual imagem do Armbian baixar

Antes de instalar o Armbian, você precisa descobrir qual é o processador da sua TV Box. É ele que define qual imagem será compatível

### Método 1 (recomendado)

1. Abra a Play Store
2. Instale o aplicativo CPU-Z ou AIDA64
3. Abra o aplicativo
4. Procure pelo campo: CPU, Hardware ou Chipset

Anote o nome do processador

### Método 2

Abra a tampa da TV Box

Na placa principal existe um chip com o nome do processador gravado em cima dele

Exemplo:

```txt
RK3229
```

### Você pode usar uma IA

Informe:

- Marca
- Modelo
- Foto da placa-mãe

Você pode utilizar o seguinte prompt:

```txt
Tenho uma TV Box da marca [MARCA] e modelo [MODELO]

Quero instalar Armbian.
```

## O que você vai precisar

- TV Box compatível
- Computador (Windows, Linux ou macOS)
- Cartão microSD de pelo menos 8 GB (NTFS)
- Adaptador USB para microSD
- Cabo HDMI
- Teclado USB
- Mouse USB
- Cabo de rede (recomendado)

## Passo 1

1. Multitool RK322x
O Multitool é responsável por inicializar a TV Box através do cartão SD e instalar o Linux

2. Armbian
Agora baixe o sistema operacional

Usei o Debian 13 Minimal, tentei usar com interface quase nem funcionava de tão lento que era

Baixe pela página:

```txt
https://armbian.com/pt/boards/rk322x-box
```

## Passo 2

- Insira o cartão microSD no adaptador PC
- Abra o Balena Etcher (Caso não funcione o balena tente usar o USBImager)
- Clique em Flash from file
- Selecione o arquivo do Multitool
- Clique em Select Target
- Escolha o cartão microSD
- Clique em Flash
- Aguarde se concluido

## Passo 3

- Não remova o cartão do computador
- Feche o Balena Etcher
- Abra o Explorador de Arquivos do seu sistema
- Você verá uma nova unidade criada chamada: **Multitool**
- Abra essa unidade
- Dentro dela existe uma pasta chamada: **images**
- Abra essa pasta
- Agora copie o arquivo do Armbian (.img.xz) para dentro dela
- Depois ejete o cartão com segurança
- Agora o cartão está pronto para ser utilizado na TV Box

## Passo 4

Com a TV Box desligada:

- Insira o cartão microSD
- Conecte o cabo HDMI
- Conecte o teclado USB
- Conecte o cabo de rede
- Ligue a TV Box

Após alguns segundos o menu do Multitool deverá aparecer

## Passo 5

No menu do Multitool:

- Escolha Burn image to internal memory (eMMC)
- Selecione a imagem do Armbian que foi copiada para a pasta images
- Aguarde o processo terminar

Quando finalizar:

- Desligue a TV Box
- Remova o cartão microSD
- Ligue novamente

## Passo 6

No primeiro boot será solicitado:

- Criação da senha do usuário root
- Criação de um usuário comum
- Senha do novo usuário
- Idioma
- Fuso horário

Após finalizar essa configuração, você terá acesso ao terminal do Armbian

## Passo 7

Conecte a TV Box à internet e execute:

```txt
sudo apt update
sudo apt upgrade -y
```

## Passo 8 (XFCE)

Para utilizar o sistema com ambiente gráfico, instale o XFCE:

```txt
sudo apt install xfce4 lightdm -y
```

Quando terminar:

```txt
sudo reboot
```

## Pronto

Agora sua TV Box está rodando Linux
