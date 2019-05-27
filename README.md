SDL-IM-plus
====

SDL �� IME �Ή��C���łł��B  
SDL 1.2.15 �� SDL-IM 1.2.8 (2005/8/28) �̃p�b�`�𓖂Ă��\�[�X��K�p���A����ɉ��_���C�����Ă��܂��B  

SDL-1.2 [README](https://github.com/nanshiki/SDL-IM-plus/blob/master/README)  

## �r���h
### Windows  
Visual Studio Professional 2015 �� VisualC/SDL.sln ��ǂݍ��݁A�r���h���Ă��������B  

### Linux  
$ ./autogen.sh  
$ ./configure  
$ make  
$ sudo make install  

Debian �n�̏ꍇ�Aapt-get �� autoconf libx11-dev libxext-dev ��������C���X�g�[�����Ă����Ă��������B  
RedHat �n�̏ꍇ�Ayum �� autoconf libXt-devel libXaw-devel ��������C���X�g�[�����Ă����Ă��������B  
���C�u�����̖��̂�w�b�_�t�@�C���̊i�[��� SDLIM �ƂȂ�܂����B  
�R���p�C���p�̊��擾�X�N���v�g�� sdlim-config �ƂȂ�܂��B  

## �ǉ��֐�
`char *SDL_SetIMValues(SDL_imvalue value, ...);`  
�@IM �̏�Ԑݒ���s���܂��B  
����: SDL_imvalue  
�@SDL_IM_ENABLE�@IM �̗L������  
�@SDL_IM_ONOFF�@IM �� ON/OFF  
�Ԓl: �G���[������ NULL�Ȃ琳��I��  
��)
`SDL_SetIMValues(SDL_IM_ENABLE, 1, NULL);`  
�@IM ��L���ɂ��܂��B

`char *SDL_GetIMValues(SDL_imvalue value, ...);`  
�@IM �̏�Ԃ��擾���܂��B  
����: SDL_imvalue  
�@SDL_IM_ENABLE�@IM �̗L������  
�@SDL_IM_ONOFF�@IM �� ON/OFF  
�Ԓl: �G���[������ NULL�Ȃ琳��I��  
��)
`SDL_GetIMValues(SDL_IM_ONOFF, &stat, NULL);`  
�@IM �� ON/OFF ��Ԃ� stat �ɓ���܂��B1 �� ON ��Ԃł��B

`int SDL_SetIMPosition(int x, int y); `  
�@IM �̕ϊ��ʒu���w�肵�܂��B  
����: x  X ���W,  y  Y ���W  
�Ԓl: 0 �ŃG���[�A����ȊO�Ő���

`int SDL_FlushIMString(void *buffer);`  
�ϊ��m�肵����������擾���܂��B  
����: buffer ��������i�[����o�b�t�@ NULL �̏ꍇ�����񒷂̂ݎ擾  
�Ԓl  ������  

## ���ϐ�
Linux �ł̏ꍇ�A���ϐ� SDLIM_STYLE �� Root, OverTheSpot, OnTheSpot �̐ݒ�����鎖�ŃA�v���P�[�V�����̕ϊ��\���̑I�����ł��܂����AOnTheSpot �ł̕ϊ�������`��ɂ͑Ή����Ă��܂���̂ł��܂�Ӗ��͂���܂���B  
���ݒ�̏ꍇ�� OverTheSpot �ƂȂ�܂��B  

## ���C�Z���X
LGPL v2  

