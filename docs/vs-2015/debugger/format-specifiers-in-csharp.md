---
title: Format Specifiers in C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3521f39227b5abcb51a4db6b61e6bf0d853e5afe
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2019
ms.locfileid: "59001261"
---
# <a name="format-specifiers-in-c"></a>Spécificateurs de format en C# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier le format dans lequel une valeur est affichée dans la fenêtre **Espion** à l’aide de spécificateurs de format. Vous pouvez également utiliser des spécificateurs de format dans la fenêtre **Exécution** , la fenêtre **Commande** et même les fenêtres sources. Si vous effectuez une suspension sur une expression dans ces fenêtres, le résultat apparaît dans un DataTip. Les DataTips répercutent le spécificateur de format dans l’affichage du DataTip.  
  
 Pour utiliser un spécificateur de format, tapez l’expression suivie par une virgule. Après la virgule, ajoutez le spécificateur approprié.  
  
## <a name="using-format-specifiers"></a>Utilisation de spécificateurs de format  
 Si vous avez le code suivant :  
  
```  
{  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Ajoutez la variable `my_var1` à la fenêtre Espion (pendant le débogage, **Déboguer / Fenêtres / Espion / Espion 1**). Ensuite, passez à l’affichage hexadécimal (dans la fenêtre **Espion** , cliquez avec le bouton droit sur la variable et sélectionnez **Affichage hexadécimal**). La fenêtre **Espion** indique à présent qu’elle contient la valeur 0x0065. Pour voir cette valeur exprimée sous la forme d’un entier décimal plutôt que sous la forme d’un entier hexadécimal, dans la colonne Nom, après le nom de la variable, ajoutez le spécificateur de format décimal : **, d**. La colonne Valeur affiche désormais la valeur décimale 101.  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Spécificateurs de format  
 Le tableau suivant montre les spécificateurs de format C# reconnus par le débogueur.  
  
|Spécificateur|Format|Valeur d’espion d’origine|Affiche|  
|---------------|------------|--------------------------|--------------|  
|ac|Force l’évaluation d’une expression. Cela peut être utile lorsque l’évaluation implicite d’appels de propriétés et de fonction implicite est désactivée. Consultez [Side Effects and Expressions](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).|Message « L’évaluation de fonction implicite est désactivée par l’utilisateur »|\<valeur>|  
|d|entier décimal|0x0065|101|  
|dynamic|Affiche l’objet spécifié à l’aide d’un affichage dynamique|Affiche tous les membres de l’objet, y compris l’affichage dynamique|Affiche uniquement l’affichage dynamique|  
|h|entier hexadécimal|61541|0x0000F065|  
|nq|chaîne sans guillemets|"Ma chaîne"|Ma chaîne|  
|hidden|Affiche tous les membres publics et non publics|Affiche les membres publics|Affiche tous les membres|  
|raw|Affiche l’élément tel qu’il apparaît dans le nœud élément brut. Valide uniquement sur les objets proxy.|Dictionnaire\<T >|Affichage brut de Dictionary\<T >|  
|résultats|Utilisé avec une variable d’un type qui implémente IEnumerable ou IEnumerable\<T >, habituellement le résultat d’une expression de requête. Affiche uniquement les membres contenant les résultats de requête.|Affiche tous les membres.|Affiche les membres qui répondent aux conditions de la requête.|  
  
## <a name="see-also"></a>Voir aussi  
 [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)   
 [Fenêtres de variables](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
