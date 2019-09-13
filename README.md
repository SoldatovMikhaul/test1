# test1
#include <iostream>
#include "PhyHead.h"
#include <SDL2/SDL.h>
#include <SDL2/SDL_ttf.h>
#include <conio.h>
#include <exception>
#include <stdio.h>
#include <clocale>
#include <string>
#include <sstream>

using namespace std;

const int SCREEN_WIDTH = 820;
const int SCREEN_HEIGHT = 480;

SDL_Window *window = nullptr;
SDL_Renderer *renderer = nullptr;

SDL_Texture* LoadImage(std::string file){
SDL_Surface *loadedImage = nullptr;
SDL_Texture *texture = nullptr;
loadedImage = SDL_LoadBMP(file.c_str());
if (loadedImage != nullptr){
texture = SDL_CreateTextureFromSurface(renderer, loadedImage);
SDL_FreeSurface(loadedImage);
}
else
std::cout << SDL_GetError() << std::endl;
return texture;
}

void ApplySurface(int x, int y, SDL_Texture *tex, SDL_Renderer *rend){
SDL_Rect pos;
pos.x = x;
pos.y = y;
SDL_QueryTexture(tex, NULL, NULL, &pos.w, &pos.h);
SDL_RenderCopy(rend, tex, NULL, &pos);
}

int main(int argc, char** argv)
{
if (SDL_Init(SDL_INIT_EVERYTHING) == -1)
{
std::cout << SDL_GetError() << std::endl;
return 1;
}
window = SDL_CreateWindow("SDL THE BEST", SDL_WINDOWPOS_CENTERED,
SDL_WINDOWPOS_CENTERED, SCREEN_WIDTH, SCREEN_HEIGHT, SDL_WINDOW_SHOWN);
if (window == nullptr)
{
std::cout << SDL_GetError() << std::endl;
return 2;
}
renderer = SDL_CreateRenderer(window, -1, SDL_RENDERER_ACCELERATED | SDL_RENDERER_PRESENTVSYNC);
if (renderer == nullptr)
{
std::cout << SDL_GetError() << std::endl;
return 3;
}
SDL_Surface* text = nullptr;
if(TTF_Init()<0) std::cout << "TTF ERROR";
SDL_Texture *number1 = nullptr, *number2 = nullptr, *number3 = nullptr, *number4 = nullptr, *number5 = nullptr, *number6 = nullptr;
number1 = LoadImage("1.bmp");
number2 = LoadImage("2.bmp");
number3 = LoadImage("3.bmp");
number4 = LoadImage("4.bmp");
number5 = LoadImage("5.bmp");
number6 = LoadImage("6.bmp");
SDL_Surface *WindSurface = nullptr;

if (number1 == nullptr || number2 == nullptr || number3 == nullptr || number4 == nullptr || number5 == nullptr || number6 == nullptr )
return 4;
SDL_RenderClear(renderer);

int bW, bH;
SDL_QueryTexture(number1, NULL, NULL, &bW, &bH);
ApplySurface(2, 2, number1, renderer);
ApplySurface(2, 42, number2, renderer);
ApplySurface(2, 84, number3, renderer);
ApplySurface(2, 126, number4, renderer);
ApplySurface(2, 168, number5, renderer);
ApplySurface(2, 210, number6, renderer);

SDL_RenderPresent(renderer);

SDL_Event event;

SDL_Rect rect= {0,0,0,0};

bool bGameLoopRunning = true;
while (bGameLoopRunning) {
    while(SDL_PollEvent(&event))

{
    if(event.key.state==SDLK_q || event.type == SDL_QUIT ) bGameLoopRunning=0;
    if(event.key.state==SDLK_r)
    {
    SDL_FillRect(WindSurface, NULL, 0x000000);

    SDL_Surface* ImageSurface1 = nullptr;
    ImageSurface1 = SDL_LoadBMP("1.bmp");
    if (ImageSurface1==nullptr) {std::cout<< SDL_GetError();}
    else
    {
    WindSurface = SDL_GetWindowSurface(window);
    rect.x=2;
    rect.y=2;
    SDL_BlitSurface(ImageSurface1,nullptr,WindSurface,&rect );
    SDL_UpdateWindowSurface(window);
        {
            if(event.type== SDL_QUIT) bGameLoopRunning=false;
        }
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {50, 2, 50, 50};
        std::string txt="otnositel'nii pokazatel' sredi dlya dvyx sred";
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }

    SDL_Surface* ImageSurface2 = nullptr;
    ImageSurface2 = SDL_LoadBMP("2.bmp");
    if (ImageSurface2==nullptr) {std::cout<< SDL_GetError();}
    else
    {
    WindSurface = SDL_GetWindowSurface(window);
    rect.x=2;
    rect.y=42;
    SDL_BlitSurface(ImageSurface2,nullptr,WindSurface,&rect );
    SDL_UpdateWindowSurface(window);
        {
            if(event.type== SDL_QUIT) bGameLoopRunning=false;
        }
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {50, 42, 50, 50};
        std::string txt="fokysnoe rasstoyanie sredi";//фокусное расстояние линзы
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }

    SDL_Surface* ImageSurface3 = nullptr;
    ImageSurface3 = SDL_LoadBMP("3.bmp");
    if (ImageSurface3==nullptr) {std::cout<< SDL_GetError();}
    else
    {
    WindSurface = SDL_GetWindowSurface(window);
    rect.x=2;
    rect.y=84;
    SDL_BlitSurface(ImageSurface3,nullptr,WindSurface,&rect );
    SDL_UpdateWindowSurface(window);
        {
            if(event.type== SDL_QUIT) bGameLoopRunning=false;
        }
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {50, 84, 50, 50};
        std::string txt="fokysnoe rasstoyanie zerkala";//фокусное расстояние зеркала
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }

    SDL_Surface* ImageSurface4 = nullptr;
    ImageSurface4 = SDL_LoadBMP("4.bmp");
    if (ImageSurface4==nullptr) {std::cout<< SDL_GetError();}
    else
    {
    WindSurface = SDL_GetWindowSurface(window);
    rect.x=2;
    rect.y=126;
    SDL_BlitSurface(ImageSurface4,nullptr,WindSurface,&rect );
    SDL_UpdateWindowSurface(window);
        {
            if(event.type== SDL_QUIT) bGameLoopRunning=false;
        }
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {50, 126, 50, 50};
        std::string txt="lineinoe yvelechenie linzi";//линейное увеличение линзы
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }

    SDL_Surface* ImageSurface5 = nullptr;
    ImageSurface5 = SDL_LoadBMP("5.bmp");
    if (ImageSurface5==nullptr) {std::cout<< SDL_GetError();}
    else
    {
    WindSurface = SDL_GetWindowSurface(window);
    rect.x=2;
    rect.y=168;
    SDL_BlitSurface(ImageSurface5,nullptr,WindSurface,&rect );
    SDL_UpdateWindowSurface(window);
        {
            if(event.type== SDL_QUIT) bGameLoopRunning=false;
        }
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {50, 168, 50, 50};
        std::string txt="yglovoe yvelechenie linzi";//угловое увеличение линзы
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }

    SDL_Surface* ImageSurface6 = nullptr;
    ImageSurface6 = SDL_LoadBMP("6.bmp");
    if (ImageSurface6==nullptr) {std::cout<< SDL_GetError();}
    else
    {
    WindSurface = SDL_GetWindowSurface(window);
    rect.x=2;
    rect.y=210;
    SDL_BlitSurface(ImageSurface6,nullptr,WindSurface,&rect );
    SDL_UpdateWindowSurface(window);
        {
            if(event.type== SDL_QUIT) bGameLoopRunning=false;
        }
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {50, 210, 50, 50};
        std::string txt="opticheskaya sila linzi";//оптическуя сила линзы
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }

    SDL_Surface* ImageSurface7 = nullptr;
    ImageSurface7= SDL_LoadBMP("7.bmp");
    if (ImageSurface7==nullptr) {std::cout<< SDL_GetError();}
    else
    {
    WindSurface = SDL_GetWindowSurface(window);
    rect.x=2;
    rect.y=252;
    SDL_BlitSurface(ImageSurface7,nullptr,WindSurface,&rect );
    SDL_UpdateWindowSurface(window);
        {
            if(event.type== SDL_QUIT) bGameLoopRunning=false;
        }
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {50, 252, 50, 50};
        std::string txt="svetosila linzi";//светосила линзы
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }


    }
    if((event.button.button == SDL_BUTTON_LEFT) && (event.button.type == SDL_MOUSEBUTTONDOWN))
    {
    if((event.button.x > 2) && (event.button.x < 42)&&(event.button.y >2) && (event.button.y <42))
    {
    //std::cout<<"otnositel'nii pokazatel' sredi dlya dvyx sred= "<<ph_nrelAbs(10,10)<<endl;
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {700, 2, 50, 50};
        double a;
        a=ph_nrelAbs(10,10);
        std::string txt;//светосила линзы
        txt=to_string(a);
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }



    else if((event.button.x > 2) && (event.button.x < 42)&&(event.button.y >44) && (event.button.y <84))
    {
     //cout<<"fokysnoe rasstoyanie sredi "<<ph_foclen(10, 10)<<endl;
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {700, 42, 50, 50};
        double a1;
        a1=ph_foclen(10, 10);
        std::string txt;//светосила линзы
        txt=to_string(a1);
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }

    else if((event.button.x > 2) && (event.button.x < 42)&&(event.button.y >86) && (event.button.y <126))
    {
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {700, 84, 50, 50};
        double a2;
        a2=ph_focmirSph(10,10);
        std::string txt;//светосила линзы
        txt=to_string(a2);
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }


    else if((event.button.x > 2) && (event.button.x < 42)&&(event.button.y >128) && (event.button.y <168))
    {
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {700, 126, 50, 50};
        double a3;
        a3=ph_linUp(10, 10);
        std::string txt;//светосила линзы
        txt=to_string(a3);
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }

    else if((event.button.x > 2) && (event.button.x < 42)&&(event.button.y >170) && (event.button.y <210))
    {

        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {700, 168, 50, 50};
        double a4;
        a4=ph_linUp(10, 10);
        std::string txt;//светосила линзы
        txt=to_string(a4);
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }


    else if((event.button.x > 2) && (event.button.x < 42)&&(event.button.y >212) && (event.button.y <254))
    {

        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {700, 210, 50, 50};
        double a5;
        a5=ph_linUp(10, 10);
        std::string txt;//светосила линзы
        txt=to_string(a5);
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }
    else if((event.button.x > 2) && (event.button.x < 42)&&(event.button.y >256) && (event.button.y <296))
    {
     //cout<<"opticheskaya sila linzi "<<ph_optPow(10)<<endl;
        SDL_Color color {255, 0, 255};
        SDL_Rect tRect = {700, 256, 50, 50};
        double a6;
        a6=ph_optPow(10);
        std::string txt;//светосила линзы
        txt=to_string(a6);
        TTF_Font * fnt = TTF_OpenFont("ALGER.ttf", 24);
        text= TTF_RenderText_Solid(fnt,txt.c_str(),color);
        SDL_BlitSurface(text,nullptr,WindSurface,&tRect );
        SDL_UpdateWindowSurface(window);
    }


    }

}
}
//SDL_Delay(10000);
SDL_DestroyTexture(number1);
SDL_DestroyTexture(number2);
SDL_DestroyTexture(number3);
SDL_DestroyTexture(number4);
SDL_DestroyTexture(number5);
SDL_DestroyTexture(number6);
SDL_DestroyRenderer(renderer);
SDL_DestroyWindow(window);
SDL_Quit();
return 0;
}
