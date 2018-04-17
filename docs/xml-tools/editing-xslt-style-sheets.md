---
title: Modification des feuilles de Style XSLT | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a228c83972c31875b9c8923922d36c9bc638380f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="editing-xslt-style-sheets"></a>Modification de feuilles de style XSLT
L'Éditeur XML permet également de modifier des feuilles de style XSLT. Vous pouvez ainsi tirer profit des fonctionnalités par défaut de l'éditeur telles qu'IntelliSense, mode plan, extraits XML, etc. Des nouvelles fonctions facilitent en outre le développement en XSLT.  
  
## <a name="xslt-features"></a>Fonctions XSLT  
 Le tableau suivant décrit les fonctionnalités spécifiques à la manipulation des feuilles de style XSLT.  
  
 **Coloration de syntaxe**  
 Mots clés XSLT, tels que `template`, `match`, et ainsi de suite, sont affichés dans la couleur de mot clé XSLT spécifiée par le **polices et couleurs** paramètres.  
  
 **Soulignements ondulés**  
 L'éditeur XML utilise le fichier installé xslt.xsd pour valider les feuilles de style XSLT. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. L'éditeur XML compile également la feuille de style en arrière-plan et signale les erreurs ou avertissements du compilateur à l'aide de soulignements ondulés appropriés.  
  
 **Prise en charge des blocs de script**  
 Le code placé dans des blocs de script est pris en charge par le débogueur XSLT ; vous pouvez donc définir des points d'arrêt et effectuer une exécution pas à pas dans le code du bloc de script.  
  
 **Afficher la sortie XSLT**  
 Vous pouvez exécuter une transformation XSL et afficher la sortie depuis l'éditeur XML. Pour plus d’informations, consultez [Comment : exécuter une Transformation XSLT à partir de l’éditeur XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).  
  
 **Débogage XSLT**  
 Vous pouvez lancer le débogueur XSLT à partir d'un fichier XSLT dans l'éditeur XML. Le débogueur prend en charge la définition de points d'arrêt dans le fichier XSLT, l'affichage de l'état d'exécution de XSLT, etc. Lorsque le pointeur est placé sur une variable XSLT, une info-bulle apparaît et affiche la valeur de la variable. Le débogueur peut permettre de déboguer une feuille de style ou une transformation XSLT compilée invoquée depuis une autre application. Pour plus d’informations, consultez [XSLT de débogage](../xml-tools/debugging-xslt.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)