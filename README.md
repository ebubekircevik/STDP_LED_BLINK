# STDP_LED_BLINK
This project is led blinks and  used Std Library with Stm32f407-Discovery Kit.

//CODES


#include "stm32f4xx.h"
#include "stm32f4_discovery.h"

GPIO_InitTypeDef GPIO_InitStruct;

void GPIO_Config(){
	RCC_AHB1PeriphClockCmd(RCC_AHB1Periph_GPIOD, ENABLE);


	GPIO_InitStruct.GPIO_Pin = GPIO_Pin_12 | GPIO_Pin_13 | GPIO_Pin_14 | GPIO_Pin_15 ;
	GPIO_InitStruct.GPIO_Mode =  GPIO_Mode_OUT;
	GPIO_InitStruct.GPIO_OType = GPIO_OType_PP;
	GPIO_InitStruct.GPIO_PuPd = GPIO_PuPd_NOPULL;
	GPIO_InitStruct.GPIO_Speed = GPIO_Speed_100MHz;

	GPIO_Init(GPIOD, &GPIO_InitStruct); //Yapılan pin ayarlarini GPIOD pinine ata
}

void delay(uint32_t time){
	//while(time--); tek satirda da yazilabilir.
	while(time>0){
		time--;
	}
}

int main(void)
{
	GPIO_Config();

  while (1)
  {
	  /*
	GPIO_SetBits(GPIOD, GPIO_Pin_12);
	GPIO_SetBits(GPIOD, GPIO_Pin_13);
	GPIO_SetBits(GPIOD, GPIO_Pin_14);
	GPIO_SetBits(GPIOD, GPIO_Pin_15);
	delay(21000000); //1 sn bekle

	GPIO_ResetBits(GPIOD, GPIO_Pin_12 | GPIO_Pin_13 | GPIO_Pin_14 | GPIO_Pin_15); //kisayol
	delay(21000000); //1 sn bekle
	   */

	  /*

	  GPIO_SetBits(GPIOD, GPIO_Pin_12);
	  delay(8000000);
	  //GPIO_ResetBits(GPIOD, GPIO_Pin_12);


	  GPIO_SetBits(GPIOD, GPIO_Pin_13);
	  delay(8000000);
	  //GPIO_ResetBits(GPIOD, GPIO_Pin_13);


	  GPIO_SetBits(GPIOD, GPIO_Pin_14);
	  delay(8000000);
	  //GPIO_ResetBits(GPIOD, GPIO_Pin_14);


	  GPIO_SetBits(GPIOD, GPIO_Pin_15);
	  delay(8000000);
	  //GPIO_ResetBits(GPIOD, GPIO_Pin_15);

	  GPIO_ResetBits(GPIOD, GPIO_Pin_12 | GPIO_Pin_13 | GPIO_Pin_14 | GPIO_Pin_15);
	  delay(8000000);
	  */
	  GPIO_ToggleBits(GPIOD, GPIO_Pin_12 | GPIO_Pin_13 | GPIO_Pin_14 | GPIO_Pin_15);
	  delay(2100000);

  }
}

void EVAL_AUDIO_TransferComplete_CallBack(uint32_t pBuffer, uint32_t Size){
  /* TODO, implement your code here */
  return;
}

uint16_t EVAL_AUDIO_GetSampleCallBack(void){
  /* TODO, implement your code here */
  return -1;
}
