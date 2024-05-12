# 7_erros_Pillow
O jogo dos 7 erros é um passatempo visual em que duas imagens aparentemente idênticas são apresentadas, mas há sete diferenças sutis entre elas. O objetivo é encontrar e marcar essas discrepâncias. Geralmente, é um desafio divertido para testar a observação e a atenção aos detalhes. 



# Importando a biblioteca Pillow para manipulação de imagens
from PIL import Image, ImageDraw


# Criando duas imagens idênticas (você pode substituir essas imagens pelas suas próprias)
imagem_original = Image.new("RGB", (300, 200), color="white")
imagem_modificada = imagem_original.copy()


# Desenhando algumas diferenças sutis na segunda imagem
draw = ImageDraw.Draw(imagem_modificada)
draw.rectangle([50, 50, 70, 70], fill="red")  # Diferença 1
draw.line([(100, 100), (120, 120)], fill="blue", width=2)  # Diferença 2


# Salvando as imagens
imagem_original.save("imagem_original.png")
imagem_modificada.save("imagem_modificada.png")


# Função para comparar as imagens e encontrar as diferenças
def encontrar_diferencas(imagem1, imagem2):
    diff = ImageChops.difference(imagem1, imagem2)
    bbox = diff.getbbox()
    return bbox


# Carregando as imagens
imagem_original = Image.open("imagem_original.png")
imagem_modificada = Image.open("imagem_modificada.png")


# Encontrando as diferenças
diferencas = encontrar_diferencas(imagem_original, imagem_modificada)


if diferencas:
    print("Encontradas diferenças nas coordenadas:", diferencas)
else:
    print("Nenhuma diferença encontrada!")


# Lembre-se de substituir as imagens acima pelas suas próprias para criar o jogo real!


Neste código, criamos duas imagens idênticas e desenhamos algumas diferenças sutis na segunda imagem. A função encontrar_diferencas compara as duas imagens e retorna as coordenadas das diferenças encontradas. Você pode personalizar as imagens e as diferenças conforme desejar.
