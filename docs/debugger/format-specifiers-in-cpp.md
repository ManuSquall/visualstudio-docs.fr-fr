---
title: "Mettre en forme les spécificateurs dans le débogueur (C++) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
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
caps.latest.revision: "40"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 11be1eb546902e8e37843383fe499274f819883f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Spécificateurs de format en C++ dans le débogueur Visual Studio
Vous pouvez modifier le format dans lequel une valeur est affichée dans la fenêtre **Espion** à l’aide de spécificateurs de format.  
  
 Vous pouvez également utiliser des spécificateurs de format dans la fenêtre **Exécution** , la fenêtre **Commande** et même les fenêtres sources. Si vous effectuez une suspension sur une expression dans ces fenêtres, le résultat apparaît dans un DataTip. L’affichage du DataTip reflète le spécificateur de format.  
  
> [!NOTE]
>  Lorsque le débogueur natif Visual Studio est passé à un nouveau moteur de débogage, certains nouveaux spécificateurs de format ont été ajoutées et certaines anciennes ont été supprimés. Le débogueur plus ancien est toujours utilisé quand vous effectuez un débogage d’interopérabilité (native et managée à la fois) avec C++/CLI. Les sections suivantes présentent les spécificateurs de format pour chaque moteur de débogage.
>   
>  -   [Spécificateurs de format](#BKMK_Visual_Studio_2012_format_specifiers) décrit les spécificateurs de format dans le nouveau moteur de débogage.  
> -   [Spécificateurs de format pour le débogage d’interopérabilité avec C++/CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) décrit les spécificateurs de format dans l’ancien moteur de débogage.  
  
## <a name="using-format-specifiers"></a>Utilisation des spécificateurs de format  
 Si vous avez le code suivant :  
  
```C++  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Ajouter le `my_var1` variable à la **espion** fenêtre (pendant le débogage, **Déboguer > Windows > espion > Espion 1**) et passez à l’affichage hexadécimal (dans le **regarder**fenêtre, avec le bouton droit de la variable et sélectionnez **affichage hexadécimal**). La fenêtre Espion indique à présent qu’elle contient la valeur 0x0065. Pour que la valeur soit exprimée sous forme de caractère plutôt que sous forme d’entier, dans la colonne Nom, après le nom de la variable, ajoutez le spécificateur de format de caractère **, c**. La colonne **Valeur** apparaît désormais avec **101 ’e’**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Spécificateurs de format  
 Les tableaux suivants indiquent les spécificateurs de format que vous pouvez utiliser dans Visual Studio. Les spécificateurs en gras ne sont pas pris en charge pour le débogage d’interopérabilité avec C++/CLI.  
  
|Spécificateur|Format|Valeur d’espion d’origine|Valeur affichée|  
|---------------|------------|--------------------------|---------------------|  
|j|entier décimal|0x00000066|102|  
|o|entier octal non signé|0x00000066|000000000146|  
|x<br /><br /> **h**|entier hexadécimal|102|0xcccccccc|  
|X<br /><br /> **H**|entier hexadécimal|102|0xcccccccc|  
|c|caractère unique|0x0065, c|101 ’e’|  
|s|chaîne const char*|\<emplacement > « hello world »|"hello world"|  
|**sb**|const char * chaîne (sans guillemets)|\<emplacement > « hello world »|hello world|  
|s8|Chaîne UTF-8|\<emplacement > « Ceci est un â˜• de tasse de café UTF-8 »|« Il s’agit d’un ☕ de tasse de café UTF-8 »|
|**s8b**|Chaîne de UTF-8 (sans guillemets)|\<emplacement > « hello world »|hello world|  
|su|Chaîne Unicode (encodage UTF-16)|\<emplacement > L « hello world »|L"hello world"<br /><br /> u"hello world"|  
|sub|Unicode (encodage UTF-16), chaîne (sans guillemets)|\<emplacement > L « hello world »|hello world|  
|bstr|chaîne BSTR|\<emplacement > L « hello world »|L"hello world"|  
|env|Bloc d’environnement (chaîne terminée par double-null)|\<emplacement > L » = :: = ::\\\\»|L "= :: = ::\\\\\\0 = C : = C :\\\\windows\\\\system32\\0ALLUSERSPROFILE =...|
|**s32**|chaîne UTF-32|\<emplacement > U « hello world »|u"hello world"|  
|**s32b**|chaîne UTF-32 (sans guillemets)|\<emplacement > U « hello world »|hello world|  
|**en**|enum|Saturday(6)|Saturday|  
|**hv**|Type de pointeur : indique que la valeur de pointeur inspectée est le résultat de l’allocation de tas d’un tableau, par exemple, `new int[3]`.|\<emplacement > {\<premier membre >}|\<emplacement > {\<premier membre >, \<deuxième membre >,...}|  
|**na**|Supprime l’adresse mémoire d’un pointeur vers un objet.|\<emplacement >, {membre = valeur...}|{membre = valeur...}|  
|**nd**|Affiche uniquement les informations de classe de base, en ignorant les classes dérivées|`(Shape*) square` inclut les informations de classe de base et de classe dérivée|Affiche uniquement les informations de classe de base|  
|hr|HRESULT ou code d’erreur Win32. (Le débogueur décodant automatiquement HRESULTs, le spécificateur n’est pas nécessaire dans ces cas-là.|S_OK|S_OK|  
|wc|Indicateur de classe de fenêtre|0x0010|WC_DEFAULTCHAR|  
|wm|Numéros de messages Windows|16|WM_CLOSE|  
|!|format brut, ignorant toutes les personnalisations d’affichage de type de données|\<personnaliser la représentation sous forme de >|4|  
  
> [!NOTE]
>  Quand le spécificateur de format **hv** est présent, le débogueur tente de déterminer la taille de la mémoire tampon et d’afficher le nombre d’éléments approprié. Comme il n’est pas toujours possible pour le débogueur de rechercher la taille exacte de la mémoire tampon d’un tableau, vous devez utiliser un spécificateur de taille `(pBuffer,[bufferSize])` chaque fois que cela est possible. Le spécificateur de format **hv** est destiné aux scénarios dans lesquels la taille de la mémoire tampon n’est pas immédiatement disponible  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Spécificateurs de taille pour les pointeurs en tant que tableaux  
 Si vous avez un pointeur vers un objet que vous souhaitez afficher sous forme de tableau, vous pouvez utiliser un entier ou une expression pour spécifier le nombre d’éléments du tableau :  
  
|Spécificateur|Format|Valeur d’espion d’origine|Valeur affichée|  
|---------------|------------|---------------------------|---------------------|  
|n|Entier décimal ou **hexadécimal**|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|Affiche `pBuffer` sous forme d’un tableau de 32 éléments.|  
|**[exp]**|Expression C++ valide qui correspond à un entier.|pBuffer,[bufferSize]|Affiche pBuffer sous forme d’un tableau d’éléments `bufferSize` .|  
|**expand(n)**|Expression C++ valide qui correspond à un entier|pBuffer, expand(2)|Affiche le troisième élément de  `pBuffer`.|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Spécificateurs de format pour le débogage d’interopérabilité avec C++/CLI  
 Les spécificateurs en **gras** sont pris en charge uniquement pour le débogage de code natif et C++/CLI.  
  
|Spécificateur|Format|Valeur d’espion d’origine|Valeur affichée|  
|---------------|------------|--------------------------|---------------------|  
|**d,i**|entier décimal signé|0xF000F065|-268373915|  
|**u**|entier décimal non signé|0x0065|101|  
|o|entier octal non signé|0xF065|0170145|  
|x,X|entier hexadécimal|61541|0x0000f065|  
|**l,h**|préfixe long ou court pour : d, i, u, o, x, X|00406042|0x0c22|  
|**f**|virgule flottante signée|(3./2.), f|1,500000|  
|**e**|notation scientifique signée|(3.0/2.0)|1.500000e+000|  
|**g**|virgule flottante signée ou notation scientifique signée, selon ce qui est le plus court|(3.0/2.0)|1,5|  
|c|caractère unique|\<emplacement >|101 ’e’|  
|s|const char*|\<emplacement >|"hello world"|  
|su|const wchar_t*<br /><br /> char16_t const\*|\<emplacement >|L"hello world"|  
|sub|const wchar_t*<br /><br /> char16_t const\*|\<emplacement >|hello world|  
|s8|const char*|\<emplacement >|"hello world"|  
|hr|HRESULT ou code d’erreur Win32. (Le débogueur décodant automatiquement HRESULTs, le spécificateur n’est pas nécessaire dans ces cas-là.|S_OK|S_OK|  
|wc|Indicateur de classe de fenêtre.|0x00000040,|WC_DEFAULTCHAR|  
|wm|Numéros de messages Windows|0x0010|WM_CLOSE|  
|!|format brut, ignorant toutes les personnalisations d’affichage de type de données|\<personnaliser la représentation sous forme de >|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Emplacements de mémoire des spécificateurs de format dans le débogage d’interopérabilité avec C++/CLI  
 Le tableau suivant contient les symboles de mise en forme pour les emplacements de mémoire. Vous pouvez utiliser un spécificateur d’emplacement de mémoire avec n’importe quelle valeur ou expression correspondant à un emplacement.  
  
|Symbole|Format|Valeur d’espion d’origine|Valeur affichée|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 caractères ASCII|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|16 octets en hexadécimal suivis de 16 caractères ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mb**|16 octets en hexadécimal suivis de 16 caractères ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mw**|8 mots|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 mots doubles|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 mots quadruples|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|caractères de 2 octets (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a>Spécificateur de taille pour les pointeurs en tant que tableaux dans le débogage d’interopérabilité avec c++ / CLI  
 Si vous avez un pointeur vers un objet que vous souhaitez afficher sous forme de tableau, vous pouvez utiliser un entier pour spécifier le nombre d’éléments du tableau :  
  
|Spécificateur|Format|Expression|Valeur affichée|  
|---------------|------------|----------------|---------------------|  
|n|entier décimal|pBuffer[32]|Affiche `pBuffer` sous forme d’un tableau de 32 éléments.|
