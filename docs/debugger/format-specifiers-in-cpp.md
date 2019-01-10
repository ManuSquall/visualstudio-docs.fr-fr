---
title: Mettre en forme spécificateurs dans le débogueur (C++) | Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 5732c7bd4f1c2fec8b7b3349d0985a2f7cbf896b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968337"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Spécificateurs de format pour C++ dans le débogueur Visual Studio
Vous pouvez modifier le format dans lequel une valeur est affichée dans le **espion** fenêtre à l’aide de spécificateurs de format.  
  
 Vous pouvez également utiliser des spécificateurs de format dans le **immédiat** fenêtre, le **commande** fenêtre, dans [des points de trace](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)et même les fenêtres sources. Si vous faites une pause d’une expression dans ces fenêtres, le résultat s’affiche dans un [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). L’affichage du DataTip reflète le spécificateur de format.  
  
> [!NOTE]
>  Lorsque le débogueur natif Visual Studio passe à un nouveau moteur de débogage, nouveaux spécificateurs de format ont été ajoutés et certains anciens ont été supprimés. Le débogueur plus ancien est toujours utilisé quand vous effectuez un débogage d’interopérabilité (native et managée à la fois) avec C++/CLI. 
  
## <a name="set-format-specifiers"></a>Spécificateurs de format de jeu  
Nous allons utiliser l’exemple de code suivant :  
  
```C++  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Ajouter le `my_var1` à la variable le **espion** fenêtre pendant le débogage, **déboguer** > **Windows** > **regarder**  >  **Espion 1**. Ensuite, avec le bouton droit de la variable et sélectionnez **affichage hexadécimal**. Maintenant le **espion** fenêtre affiche la valeur 0 x 0065. Pour afficher cette valeur exprimée sous la forme d’un caractère plutôt qu’un entier, tout d’abord avec le bouton droit et désélectionnez **affichage hexadécimal**. Puis ajoutez le spécificateur de format de caractère **, c** dans le **nom** colonne après le nom de variable. Le **valeur** colonne affiche maintenant **101 'e'**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Spécificateurs de format  
 Les tableaux suivants décrivent les spécificateurs de format que vous pouvez utiliser dans Visual Studio. Les spécificateurs en gras sont uniquement compatible avec le nouveau débogueur et ne pas pour le débogage d’interopérabilité avec C++ / c++ / CLI.  
  
|Spécificateur|Format|Valeur d’espion d’origine|Valeur affichée|  
|---------------|------------|--------------------------|---------------------|  
|d|entier décimal|0x00000066|102|  
|o|entier octal non signé|0x00000066|000000000146|  
|x<br /><br /> **h**|entier hexadécimal|102|0xcccccccc|  
|X<br /><br /> **H**|entier hexadécimal|102|0xcccccccc|  
|c|caractère unique|0x0065, c|101 ’e’|  
|s|const char * chaîne (avec les guillemets)|\<emplacement > « hello world »|"hello world"|  
|**sb**|const char* chaîne (sans guillemets)|\<emplacement > « hello world »|hello world|  
|s8|Chaîne UTF-8|\<emplacement > « Ceci est un â˜• tasse de café de UTF-8 »|« Il s’agit d’un ☕ tasse de café de UTF-8 »|
|**s8b**|chaîne UTF-8 (sans guillemets)|\<emplacement > « hello world »|hello world|  
|su|Chaîne Unicode (encodage UTF-16) (avec les guillemets)|\<emplacement > L « hello world »|L"hello world"<br /><br /> u"hello world"|  
|sub|chaîne Unicode (encodage UTF-16) (sans guillemets)|\<emplacement > L « hello world »|hello world|  
|bstr|Chaîne binaire de BSTR (avec les guillemets)|\<emplacement > L « hello world »|L"hello world"|  
|env|Bloc d’environnement (chaîne finissant par une double valeur null)|\<emplacement > L "= :: = ::\\\\»|L "= :: = ::\\\\\\0 = C : = C :\\\\windows\\\\system32\\0ALLUSERSPROFILE =...|
|**s32**|Chaîne UTF-32 (avec les guillemets)|\<emplacement > U « hello world »|u"hello world"|  
|**s32b**|chaîne UTF-32 (sans guillemets)|\<emplacement > U « hello world »|hello world|  
|**en**|enum|Saturday(6)|Saturday|  
|**hv**|Type de pointeur : indique que la valeur de pointeur inspectée est le résultat de l’allocation de tas d’un tableau, par exemple, `new int[3]`.|\<emplacement>{\<premier membre>}|\<emplacement > {\<premier membre >, \<deuxième membre >,...}|  
|**na**|Supprime l’adresse mémoire d’un pointeur vers un objet.|\<emplacement>, {membre=valeur...}|{membre=valeur…}|  
|**nd**|Affiche uniquement les informations de classe de base, en ignorant les classes dérivées|`(Shape*) square` inclut les informations de classe de base et de classe dérivée|Affiche uniquement les informations de classe de base|  
|hr|HRESULT ou code d’erreur Win32. Ce spécificateur n’est plus nécessaire pour les valeurs HRESULT comme le débogueur les décode automatiquement.|S_OK|S_OK|  
|wc|Indicateur de classe de fenêtre|0x0010|WC_DEFAULTCHAR|  
|wm|Numéros de messages Windows|16|WM_CLOSE|  
|!|format brut, ignorant toutes les personnalisations d’affichage de type de données|\<représentation personnalisée>|4|  
  
> [!NOTE]
>  Lorsque le **hv** spécificateur de format est présent, le débogueur tente de déterminer la longueur de la mémoire tampon et afficher ce nombre d’éléments. Comme il n’est pas toujours possible pour le débogueur de rechercher la taille exacte de la mémoire tampon d’un tableau, vous devez utiliser un spécificateur de taille `(pBuffer,[bufferSize])` chaque fois que cela est possible. Le **hv** spécificateur de format est utile lorsque la taille du tampon n’est pas immédiatement disponible  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Spécificateurs de taille pour les pointeurs en tant que tableaux  
 Si vous avez un pointeur vers un objet que vous voulez afficher sous forme de tableau, vous pouvez utiliser un entier ou une expression pour spécifier le nombre d’éléments du tableau. 
  
|Spécificateur|Format|Valeur d’espion d’origine|Valeur affichée|  
|---------------|------------|---------------------------|---------------------|  
|n|Entier décimal ou **hexadécimal**|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|Affiche `pBuffer` sous forme d’un tableau de 32 éléments.|  
|**[exp]**|Expression C++ valide qui correspond à un entier.|pBuffer,[bufferSize]|Affiche pBuffer sous forme d’un tableau d’éléments `bufferSize` .|  
|**expand(n)**|Expression C++ valide qui correspond à un entier|pBuffer, expand(2)|Affiche le troisième élément de  `pBuffer`.|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Spécificateurs de format pour le débogage d’interopérabilité avec C++/CLI  
 Les spécificateurs en **gras** sont pris en charge uniquement pour le débogage de code natif et C++/CLI.  
  
|Spécificateur|Format|Valeur d’espion d’origine|Valeur affichée|  
|---------------|------------|--------------------------|---------------------|  
|**d**<br /><br />**i**|entier décimal signé|0xF000F065|-268373915|  
|**u**|entier décimal non signé|0x0065|101|  
|o|entier octal non signé|0xF065|0170145|  
|x<br /><br />X|entier hexadécimal|61541|0x0000f065|  
|**l**<br /><br />**h**|préfixe long ou court pour : d, i, u, o, x, X|00406042|0x0c22|  
|**f**|virgule flottante signée|(3./2.), f|1,500000|  
|**e**|notation scientifique signée|(3.0/2.0)|1.500000e+000|  
|**g**|virgule flottante signée ou notation scientifique signée,<br/> selon ce qui est plus court|(3.0/2.0)|1,5|  
|c|caractère unique|\<emplacement>|101 ’e’|  
|s|const char * (avec les guillemets)|\<emplacement>|"hello world"|  
|su|const wchar_t*<br /><br /> char16_t const\* (avec les guillemets)|\<emplacement>|L"hello world"|  
|sub|const wchar_t*<br /><br /> const char16_t\*|\<emplacement>|hello world|  
|s8|const char * (avec les guillemets)|\<emplacement>|"hello world"|  
|hr|HRESULT ou code d’erreur Win32.<br/>Ce spécificateur n’est plus nécessaire pour les valeurs HRESULT comme le débogueur les décode automatiquement.|S_OK|S_OK|  
|wc|Indicateur de classe de fenêtre|0x00000040,|WC_DEFAULTCHAR|  
|wm|Numéros de messages Windows|0x0010|WM_CLOSE|  
|!|format brut, ignorant les personnalisations de vue de type de données|\<représentation personnalisée>|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Spécificateurs pour les emplacements de mémoire de débogage d’interopérabilité avec C++ / de format c++ / CLI  
 Le tableau suivant décrit les symboles de mise en forme pour les emplacements de mémoire. Vous pouvez utiliser un spécificateur d’emplacement de mémoire avec n’importe quelle valeur ou expression correspondant à un emplacement.  
  
|Symbole|Format|Valeur d’espion d’origine|Valeur affichée|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 caractères ASCII|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|16 octets en hexadécimal suivis de 16 caractères ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mb**|16 octets en hexadécimal suivis de 16 caractères ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mw**|8 mots|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 mots doubles|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 mots quadruples|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|caractères de 2 octets (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Spécificateur de taille pour les pointeurs en tant que tableaux dans le débogage d’interopérabilité avec C++/CLI  
 Si vous avez un pointeur vers un objet que vous voulez afficher sous forme de tableau, vous pouvez utiliser un entier pour spécifier le nombre d’éléments du tableau.
  
|Spécificateur|Format|Expression|Valeur affichée|  
|---------------|------------|----------------|---------------------|  
|n|entier décimal|pBuffer[32]|Affiche `pBuffer` sous forme de tableau de 32 éléments.|
