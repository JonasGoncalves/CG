# Introdução à Computação Gráfica

## Antonio Jonas G. de Oliveira
## Thiago Alves de Araujo

# Sumário
* [Introdução](#introdução)
* [Framework](#framework)
* [Funções Propostas](#funções-propostas)
	* [PutPixel](#PutPixel)
	* [DrawLine](#DrawLine)
	* [DrawTriangle](#DrawTriangle)
* [Conclusão](#conclusão)
* [Referencias](#referencias)
---

## Introdução

Esse relatório busca mostrar como foi desenvolvido o primeiro trabalho da dicisplina de Introdução a Computação Gráfica, utilizando de um framework fornecido pelo professor e propor o desenvolvimento de três funções referentes ao tema de rasterização.

---

## Framework

O framework usado, foi disponibilizado pelo professor, e permite que o aluno consiga, atraves de uma simulação, acessar a memoria para efetuar as operações necessárias, visto que os SO não permitem que o usuário tenha esse acesso.

---

### Funções Propostas
Era necessário a implementação de três funções usando o algoritmo de rasterização de Bresenham, que cria linhas em dispositivos matriciais, permitindo a determinação de quais são os pontos numa matriz de base quadrada que devemm ser destacados com o intuito de atender o grau de inclinação de ângulo.
Inicialmente será feito a implementação da função PutPixel.

#### PutPixel
Sabemos que o Pixel é o menor elemento em um dispositivo de exibição (como por exemplo o monitor), em que podemos designar uma cor (RGB), e um grau de transparência (Alpha). Ele é o menor ponto que forma uma imagem.

A seguir veremos como foi implementado a função PutPixel na linguagem C.

```C++

	void PutPixel(int x, int y, unsigned char R, unsigned char G, unsigned char B, unsigned char A){
	
	//Verifica se o ponto está dentro da janela
	if(x > IMAGE_WIDTH || x <  0  || y > IMAGE_HEIGHT || y <  0)
		return;
	
	//Define o offset
	int offset = (x*4) + (y*4*IMAGE_WIDTH);

	//Escreve o ponto na memória
	fb_ptr[offset + 0] = R;
	fb_ptr[offset + 1] = G;
	fb_ptr[offset + 2] = B;
	fb_ptr[offset + 3] = A;
}

```

A função a cima possui:

>1. (X,Y) é a coordenada das posições que deve ser desenhada na tela.
>2. RGBA diz respeito as cores.


<p align="center">
	<br>
	<img src="./img/putPixel.PNG"/ width=510px height=540px>
	<h5 align="center">Figure 2 - Pixel vermelho desenhado na tela</h5>
	<br>
</p>

---

#### DrawLine

O drawnline irá utilizar uma variação do algoritmo de Bresenham, que pegará dois pontos e criará uma linha, em angulações diversas, e as linhas possuem cores variadas, através da interpolação linear.

O código a seguir mostra como foi feito a função DrawLine em C.

```C++
coming soon

```

<p align="center">
	<br>
	<img src="./img/drawline.PNG"/ width=510px height=540px>
	<h5 align="center">Figure 3 - Linha desenhada com Bresenham</h5>
	<br>
</p>

---

#### DrawTriangle

Com a criação do DrawLine, para criar o triângulo precisa somente definir três retas. A seguir podemos ver como ficou a função na linguagem C.

```C++

 
}
```
<p align="center">
	<br>
	<img src="./img/drawtriangle.PNG"/ width=510px height=540px>
	<h5 align="center">Figure 4 - Representação de um triangulo</h5>
	<br>
</p>

---
## Conclusão

### Resultados
Como podemos observar, o trabalho conseguiu cumprir seus objetivos, conseguindo desenhar pontos, retas e triângulos, com as cores variando, através da interpolação linear.

### Desafios

O maior desafio foi adaptar o algoritmo de Bresenham, que funciona apenas para um octante, e conseguir generalizar o algoritmo para que consiga resolver todas as situações dos oito octantes.

---

### Referências