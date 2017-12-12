---
redirect_url: /visualstudio/ide/logical-operators-in-search-expressions
ms.openlocfilehash: fe896af873197c95a4b226396e0b6333fdc40cfa
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
title: "Opérateurs de recherche avancée dans les expressions de recherche | Microsoft Docs" ms.custom: "" ms.date: "06/02/2017" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "Help Viewer, recherche de mots clés"
  - "Help Viewer, recherche de code"
  - "Help Viewer, recherche de code par langage de programmation"
  - "Help Viewer, recherche de titres"
  - "recherche de code [Help Viewer]"
  - "recherche de titres [Help Viewer]" ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e caps.latest.revision: 9 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="advanced-search-operators-in-search-expressions"></a>Opérateurs de recherche avancée dans les expressions de recherche
En utilisant des opérateurs de recherche avancée dans Help Viewer, vous pouvez affiner votre recherche de contenu en spécifiant à quel endroit rechercher un terme dans une rubrique. Le tableau suivant décrit les quatre opérateurs de recherche avancée disponibles.

|Pour rechercher|Utilisez|Exemple|Résultat|  
|-------------------|---------|-------------|------------|  
|Un terme dans le titre de la rubrique|title:|title:binaryreader|Rubriques qui contiennent « binaryreader » dans leur titre.|  
|Un terme dans un exemple de code|code:|code:readdouble|Rubriques qui contiennent « readdouble » dans un exemple de code.|  
|Un terme dans un exemple de langage de programmation spécifique|code:vb:|code:vb:string|Rubriques qui contiennent « string » dans un exemple de code Visual Basic.|  
|Une rubrique qui est associée à un mot clé d’index spécifique|keyword:|keyword:readbyte|Rubriques associées au mot clé d’index « readbyte ».|  

> [!WARNING]
>  Vous devez entrer les opérateurs de recherche avancée avec un signe deux-points final et sans espace avant ce signe pour que le moteur de recherche les identifie.    

## <a name="programming-languages-for-code-examples"></a>Langages de programmation des exemples de code
Vous pouvez utiliser l’opérateur code: pour rechercher du contenu sur l’un des différents langages de programmation, mais cet opérateur retourne des résultats uniquement pour le contenu marqué avec un libellé de langage de programmation. Si vous voulez retourner des exemples pour un langage de programmation spécifique, utilisez l’une des valeurs de langage de programmation suivantes :  

|Langage de programmation|Syntaxe de l’opérateur de recherche|  
|--------------------|---------|  
|Visual Basic|code:vb<br/>code:visualbasic|  
|C#|code:c#<br/>code:csharp|  
|C++|code:cpp<br/>code:c++<br/>code:cplusplus|  
|F#|code:f#<br/>code:fsharp|  
|JavaScript|code:javascript<br/>code:js|  
|XAML|code:xaml|
