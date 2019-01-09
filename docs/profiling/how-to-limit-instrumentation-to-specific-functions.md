---
title: 'Procédure : Limiter l’instrumentation à des fonctions spécifiques | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0135ea7d3a99f54b8bc61fb77c5b1657992033c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895056"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Procédure : Limiter l’instrumentation à des fonctions spécifiques
Vous pouvez limiter l’instrumentation et la collecte de données à une ou plusieurs fonctions en configurant des options dans la page **Avancé** de la **Session de performance** ou dans les pages de propriétés des fichiers binaires cibles :  
  
- Si vous spécifiez des fonctions dans la page de propriétés de la session de performance, seules ces fonctions seront instrumentées dans tous les fichiers binaires instrumentés de la session.  
  
- Si vous spécifiez des fonctions dans la page de propriétés d’un fichier binaire cible, seules les fonctions qui figurent dans ce fichier binaire seront instrumentées. Les fonctions des autres fichiers binaires de la session performance sont instrumentées normalement.  
  
  Le fait de limiter ainsi la collecte de données est possible uniquement lorsque la méthode de profilage par instrumentation est sélectionnée.  
  
> [!NOTE]
>  Vous pouvez également utiliser la page **Avancé** des pages de propriétés **Session de performance** pour définir d’autres options qui sont disponibles dans l’outil d’instrumentation en ligne de commande [VSInstr](../profiling/vsinstr.md) des outils de profilage.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Pour limiter l’instrumentation à certaines fonctions dans une session de performance  
  
1. Dans l’**Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session, puis cliquez sur **Propriétés**.  
  
    La boîte de dialogue **Pages de propriétés** s’affiche.  
  
2. Dans la boîte de dialogue **Pages de propriétés**, cliquez sur **Avancé**.  
  
3. Dans la zone de texte **Options d’instrumentation supplémentaires**, utilisez la syntaxe suivante pour taper le nom des fonctions que vous voulez instrumenter :  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` correspond au nom de l’espace de noms et de la fonction. Son format est le suivant : `Namespace`**::**`FunctionName`. Utilisez un point-virgule pour séparer les fonctions. Utilisez un astérisque (\*) pour spécifier un caractère générique pour un ou plusieurs caractères. Par exemple, **/include:MyNS::\\*** spécifie toutes les fonctions de l’espace de noms MyNS.  
  
   > [!NOTE]
   >  Pour répertorier les fonctions d’un fichier binaire, ouvrez une fenêtre d’invite de commandes dans le répertoire d’installation des outils de profilage (consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)), puis tapez **vsinstr /DumpFuncs**  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Pour limiter l’instrumentation à certaines fonctions d’un fichier binaire  
  
1. Dans l’**Explorateur de performances**, recherchez le nom du fichier binaire sous le nœud **Cibles** de la session de performance.  
  
2. Cliquez avec le bouton droit sur le nom du fichier binaire, puis cliquez sur **Propriétés**.  
  
    La boîte de dialogue **Pages de propriétés** s’affiche.  
  
3. Dans la boîte de dialogue **Pages de propriétés**, cliquez sur **Avancé**.  
  
4. Dans la zone de texte **Options d’instrumentation supplémentaires**, utilisez la syntaxe suivante pour taper le nom des fonctions que vous voulez instrumenter :  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` correspond au nom de l’espace de noms et de la fonction. Son format est le suivant : `Namespace`**::**`FunctionName`. Utilisez un point-virgule pour séparer les fonctions. Utilisez un astérisque (\*) pour spécifier un caractère générique pour un ou plusieurs caractères. Par exemple, **/include:MyNS::\\*** spécifie toutes les fonctions de l’espace de noms MyNS.  
  
   > [!NOTE]
   >  Pour répertorier les fonctions d’un fichier binaire, ouvrez une fenêtre d’invite de commandes dans le répertoire d’installation des outils de profilage (consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)), puis tapez **vsinstr /DumpFuncs**  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler la collecte des données](../profiling/controlling-data-collection.md)   
 [Guide pratique pour limiter l’instrumentation à des DLL spécifiques](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Guide pratique pour spécifier des options d’instrumentation supplémentaires](../profiling/how-to-specify-additional-instrumentation-options.md)