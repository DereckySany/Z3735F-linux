# Z3735F-linux
Linux no [Intel(R) Atom(TM) CPU Z3735F](http://ark.intel.com/products/80274/Intel-Atom-Processor-Z3735F-2M-Cache-up-to-1_83-GHz), bay trail


### Uma CPU de 64 bits forçada a trabalhar em um sistema operacional de 32 bits, o que a EFI importa?
A CPU suporta conjuntos de instruções de 64 bits, os fornecedores vendem produtos com SO de 32 bits, inicializados por um EFI de 32 bits.
- EFIshell.ia32 pode carregar aplicativos EFI de 32 bits
- GRUB2 pode ser construído como aplicativo EFI de 32/64 bits
- Depois de ter o GRUB2, você pode inicializar um sistema operacional de 64 bits

## GRUB
* Construindo o ALVO:
```
$ grub-mkimage -C xz -o grub2ia32.efi -O i386-efi -p /usr/lib/grub/i386-efi/*.mod
$ file grub2ia32.efi
grub2ia32.efi: PE32 executable (EFI application) Intel 80386 (stripped to external PDB), for MS Windows
```
---
### Usando:
***WINDOWS***
* Mova-o para uma partição HDD, no meu caso C:\myefi abaixo é compartilhado e de propriedade do meu usuário, partição do sistema NTFS.
```
mount.cifs //192.168.1.*/myefi /mnt/cifs -o username=*,password=*,file_mode=0777,dir_mode=0777
mv grub2ia32.efi /mnt/cifs/
```
---
## Carregando GRUB
* Entre no BIOS, inicie o shell EFI
* Execute o GRUB, inserindo o PATH completo

-----------------------------

# Z3735F-linux
linux on [Intel(R) Atom(TM) CPU Z3735F](http://ark.intel.com/products/80274/Intel-Atom-Processor-Z3735F-2M-Cache-up-to-1_83-GHz), Bay Trail


### A 64bit CPU forced working in a 32bit OS, what EFI matters?
CPU is supporting 64bit intruction sets, vendors sell products running 32bit OS, booted by a 32bit EFI.  
- EFIshell.ia32 can load 32bit EFI applications  
- GRUB2 can be built as 32/64bit EFI application  
- Once you have GRUB2, you can boot a 64bit OS  

## GRUB
* Build our TARGET:
```
$ grub-mkimage -C xz -o grub2ia32.efi -O i386-efi -p /usr/lib/grub/i386-efi/*.mod
$ file grub2ia32.efi
grub2ia32.efi: PE32 executable (EFI application) Intel 80386 (stripped to external PDB), for MS Windows
```
* Move it to one HDD partition, in my case C:\myefi below is shared and owned by my usermane, NTFS system partition.  
```
mount.cifs //192.168.1.*/myefi /mnt/cifs -o username=*,password=*,file_mode=0777,dir_mode=0777
mv grub2ia32.efi /mnt/cifs/
```

## Loading GRUB
* Enter BIOS, lauch EFI shell
* Execute GRUB, by entering full PATH
