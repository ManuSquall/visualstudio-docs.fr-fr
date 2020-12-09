---
title: Spécificateurs de format dans le débogueur (C#) | Microsoft Docs
description: Utilisez un spécificateur de format pour modifier le format dans lequel une valeur est affichée dans le Fenêtre Espion. Cet article fournit des détails sur l’utilisation.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 31739b9c8fecc862c891173a792986b467730400
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862787"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Spécificateurs de format en C# dans le débogueur Visual Studio
Vous pouvez modifier le format dans lequel une valeur est affichée dans la fenêtre **Espion** à l’aide de spécificateurs de format. Vous pouvez également utiliser des spécificateurs de format dans la fenêtre **exécution** , la fenêtre **commande** , les points de [trace](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)et les fenêtres sources. Si vous faites une pause sur une expression dans ces fenêtres, le résultat s’affiche dans un  [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) dans l’affichage de format spécifié.

Pour utiliser un spécificateur de format, entrez l’expression de variable suivie d’une virgule et du spécificateur approprié.

## <a name="set-format-specifiers"></a>Définir des spécificateurs de format
Nous allons utiliser l’exemple de code suivant :

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Ajoutez la `my_var1` variable à la fenêtre **Espion** pendant le débogage, puis **déboguez**  >  **Windows**  >  **Watch**  >  **Espion 1**. Ensuite, cliquez avec le bouton droit sur la variable et sélectionnez **affichage hexadécimal**. À présent, la fenêtre **Espion** affiche la valeur 0x0065. Pour afficher cette valeur sous la forme d’un entier décimal plutôt que sous la forme d’un entier hexadécimal, ajoutez le spécificateur de format décimal **, d** dans la colonne **nom** après le nom de la variable. La colonne **valeur** affiche maintenant **101**.

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

::: moniker range=">= vs-2019" 

Vous pouvez afficher et sélectionner dans une liste de spécificateurs de format disponibles en ajoutant une virgule (,) à la valeur dans la fenêtre **Espion** . 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>Spécificateurs de format
Le tableau suivant décrit les spécificateurs de format C# pour le débogueur Visual Studio.

|Spécificateur|Format|Valeur d’espion d’origine|Affiche|
|---------------|------------|--------------------------|--------------|
|clim|Force l’évaluation d’une expression, qui peut être utile lorsque l’évaluation implicite des propriétés et des appels de fonction implicite est désactivée.|Message « L’évaluation de fonction implicite est désactivée par l’utilisateur »|\<value>|
|d|entier décimal|0x0065|101|
|dynamique|Affiche l’objet spécifié à l’aide d’un affichage dynamique|Affiche tous les membres de l’objet, y compris l’affichage dynamique|Affiche uniquement l’affichage dynamique|
|h|entier hexadécimal|61541|0x0000F065|
|nq|chaîne sans guillemets|"Ma chaîne"|Ma chaîne|
|NSE|Spécifie le comportement, et non le format. Évalue l’expression avec « aucun effet secondaire ». Si l’expression ne peut pas être interprétée et ne peut être résolue que par une évaluation (par exemple, un appel de fonction), une erreur s’affiche à la place.|N/A|N/A|
|hidden|Affiche tous les membres publics et non publics|Affiche les membres publics|Affiche tous les membres|
|raw|Affiche l’élément tel qu’il apparaît dans le nœud élément brut. Valide uniquement sur les objets proxy.|Dictionnaire\<T>|Affichage brut du dictionnaire\<T>|
|results|Utilisé avec une variable d’un type qui implémente IEnumerable ou IEnumerable \<T> , habituellement le résultat d’une expression de requête. Affiche uniquement les membres contenant les résultats de requête.|Affiche tous les membres|Affiche les membres qui répondent aux conditions de la requête|

## <a name="see-also"></a>Voir aussi
- [Fenêtres espion et espion Express](../debugger/watch-and-quickwatch-windows.md)
- [Fenêtres automatique et variables locales](../debugger/autos-and-locals-windows.md)
