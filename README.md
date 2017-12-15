CONSTANTS.H

#pragma once
#ifndef CONSTANTS_H
#define CONSTANTS_H

namespace constants
{
	const double gravitity{ 9.8 };

}
#endif 


MAIN.CPP

#include "stdafx.h"
#include "constants.h"
#include <iostream>

//pede a altura do usuario
double getAlturaInicial()
{	
	std::cout << "Altura inicial: ";
	double alturaInicial;
	std::cin >> alturaInicial;
	return alturaInicial;
}

//calcula a distancia depois de X segundos
double calcularAlturaAtual(double alturaInicial, int segundos) 
{
	double distanciaQueda = (constants::gravitity * (segundos*segundos)) / 2;
	double alturaAtual = alturaInicial - distanciaQueda;
	return alturaAtual;
}

//imprimir e checar se chegou ao chao
void imprimir(double altura, int segundos)
{
	if (altura>0.0)
	{
		std::cout << "Em " << segundos << " segundos o objeto esta a " << altura << " do chao\n";
	}
	else 
	{
		std::cout << "Em " << segundos << " segundos o objeto esta no chao\n";
	}
}

//chama a "calcularAlturaAtual" para entrar na condição do "imprimir"
void calculareImprimir(double alturaInicial, int segundos)
{
	double altura = calcularAlturaAtual(alturaInicial, segundos);
	imprimir(altura, segundos);
}

int main() 
{
	const double alturaInicial = getAlturaInicial();
	int cont = 0;
	double altura;
	do 
	{
		calculareImprimir(alturaInicial, cont);
		altura = calcularAlturaAtual(alturaInicial, cont);
		cont++;
	} while (altura> 0.0);
	

	return 0;
}
