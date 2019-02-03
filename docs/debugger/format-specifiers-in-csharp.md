---
title: Dans le débogueur, les spécificateurs de format (C#) | Microsoft Docs
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe922960b0571593cc15581c29244798fd0f671e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018733"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Dans les spécificateurs de format C# dans le débogueur Visual Studio
Vous pouvez modifier le format dans lequel une valeur est affichée dans le **espion** fenêtre à l’aide de spécificateurs de format. Vous pouvez également utiliser des spécificateurs de format dans le **immédiat** fenêtre, le **commande** fenêtre, dans [des points de trace](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)et dans les fenêtres sources. Si vous faites une pause d’une expression dans ces fenêtres, le résultat s’affiche dans un [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) dans l’affichage du format spécifié.  
  
 Pour utiliser un spécificateur de format, entrez l’expression de variable suivie par une virgule et le spécificateur approprié.  
  
## <a name="set-format-specifiers"></a>Spécificateurs de format de jeu  
Nous allons utiliser l’exemple de code suivant :   
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Ajouter le `my_var1` à la variable le **espion** fenêtre pendant le débogage, **déboguer** > **Windows** > **regarder**  >  **Espion 1**. Ensuite, avec le bouton droit de la variable et sélectionnez **affichage hexadécimal**. Maintenant le **espion** fenêtre affiche la valeur 0 x 0065. Pour afficher cette valeur comme un entier décimal plutôt qu’un entier hexadécimal, ajoutez le spécificateur de format décimal **, d** dans le **nom** colonne après le nom de variable. Le **valeur** colonne affiche maintenant **101**.   
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Spécificateurs de format  
 Le tableau suivant décrit les C# spécificateurs pour le débogueur Visual Studio de format.  
  
|Spécificateur|Format|Valeur d’espion d’origine|Affiche|  
|---------------|------------|--------------------------|--------------|  
|ac|Forcer l’évaluation d’une expression qui peut être utile lors de l’évaluation implicite de propriétés et appels de fonction implicite est désactivée.|Message « L’évaluation de fonction implicite est désactivée par l’utilisateur »|\<valeur>|  
|d|entier décimal|0x0065|101|  
|dynamic|Affiche l’objet spécifié à l’aide d’un affichage dynamique|Affiche tous les membres de l’objet, y compris l’affichage dynamique|Affiche uniquement l’affichage dynamique|  
|h|entier hexadécimal|61541|0x0000F065|  
|nq|chaîne sans guillemets|"Ma chaîne"|Ma chaîne|  
|NSE|Spécifie le comportement, pas de format. Évalue l’expression « Sans effets secondaires ». Si l’expression ne peut pas être interprétée et peut uniquement être résolue en un formulaire d’évaluation (par exemple, un appel de fonction), une erreur s’affiche à la place.|N/A|N/A|
|hidden|Affiche tous les membres publics et non publics|Affiche les membres publics|Affiche tous les membres|  
|raw|Affiche l’élément tel qu’il apparaît dans le nœud élément brut. Valide uniquement sur les objets proxy.|Dictionnaire\<T >|Affichage brut de Dictionary\<T >|  
|résultats|Utilisé avec une variable d’un type qui implémente IEnumerable ou IEnumerable\<T >, habituellement le résultat d’une expression de requête. Affiche uniquement les membres contenant les résultats de requête.|Affiche tous les membres|Affiche les membres qui répondent aux conditions de la requête|  
  
## <a name="see-also"></a>Voir aussi  
 [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)   
 [Fenêtres Variables locales et Automatique](../debugger/autos-and-locals-windows.md)
