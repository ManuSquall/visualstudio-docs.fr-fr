---
title: "Modification de feuilles de style XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Modification de feuilles de style XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'Éditeur XML permet également de modifier des feuilles de style XSLT.Vous pouvez ainsi tirer profit des fonctionnalités par défaut de l'éditeur telles qu'IntelliSense, mode plan, extraits XML, etc.Des nouvelles fonctions facilitent en outre le développement en XSLT.  
  
## Fonctions XSLT  
 Le tableau suivant décrit les fonctions spécifiques à la manipulation des feuilles de style XSLT.  
  
 **Mise en couleur de la syntaxe**  
 Les mots clés XSLT, tels que `template`, `match`, etc., s'affichent dans la couleur de mot clé XSLT spécifiée dans les paramètres **Polices et couleurs**.  
  
 **Soulignements ondulés**  
 L'éditeur XML utilise le fichier installé xslt.xsd pour valider les feuilles de style XSLT.Les erreurs de validation sont indiquées par des soulignements ondulés bleus.L'éditeur XML compile également la feuille de style en arrière\-plan et signale les erreurs ou avertissements du compilateur à l'aide de soulignements ondulés appropriés.  
  
 **Prise en charge des blocs de script**  
 Le code placé dans des blocs de script est pris en charge par le débogueur XSLT ; vous pouvez donc définir des points d'arrêt et effectuer une exécution pas à pas dans le code du bloc de script.  
  
 **Affichage de la sortie XSLT**  
 Vous pouvez exécuter une transformation XSL et afficher la sortie depuis l'éditeur XML.Pour plus d'informations, consultez [Procédure : exécuter une transformation XSLT à partir de l'Éditeur XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).  
  
 **Débogage XSLT**  
 Vous pouvez lancer le débogueur XSLT à partir d'un fichier XSLT dans l'éditeur XML.Le débogueur prend en charge la définition de points d'arrêt dans le fichier XSLT, l'affichage de l'état d'exécution de XSLT, etc.Lorsque le pointeur est placé sur une variable XSLT, une info\-bulle apparaît et affiche la valeur de la variable.Le débogueur peut permettre de déboguer une feuille de style ou une transformation XSLT compilée invoquée depuis une autre application.Pour plus d'informations, consultez [Débogage XSLT](../xml-tools/debugging-xslt.md).  
  
## Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)