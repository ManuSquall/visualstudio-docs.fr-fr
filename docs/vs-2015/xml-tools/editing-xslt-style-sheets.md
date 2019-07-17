---
title: Modification des feuilles de Style XSLT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2279a193b173924b45f42172281e106370131023
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157738"
---
# <a name="editing-xslt-style-sheets"></a>Modification de feuilles de style XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'Éditeur XML permet également de modifier des feuilles de style XSLT. Vous pouvez ainsi tirer profit des fonctionnalités par défaut de l’éditeur telles qu’IntelliSense, mode plan, extraits XML, etc. Des nouvelles fonctionnalités facilitent en outre le développement en XSLT.  
  
## <a name="xslt-features"></a>Fonctionnalités XSLT  
 Le tableau suivant décrit les fonctions spécifiques à la manipulation des feuilles de style XSLT.  
  
 **La coloration syntaxique**  
 Mots clés XSLT, tels que `template`, `match`, et ainsi de suite, sont affichés dans la couleur de mot clé XSLT spécifiée par le **polices et couleurs** paramètres.  
  
 **Soulignements ondulés**  
 L'éditeur XML utilise le fichier installé xslt.xsd pour valider les feuilles de style XSLT. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. L'éditeur XML compile également la feuille de style en arrière-plan et signale les erreurs ou avertissements du compilateur à l'aide de soulignements ondulés appropriés.  
  
 **Prise en charge des blocs de script**  
 Le code placé dans des blocs de script est pris en charge par le débogueur XSLT ; vous pouvez donc définir des points d'arrêt et effectuer une exécution pas à pas dans le code du bloc de script.  
  
 **Afficher la sortie XSLT**  
 Vous pouvez exécuter une transformation XSL et afficher la sortie depuis l'éditeur XML. Pour plus d’informations, consultez [Guide pratique pour Exécuter une Transformation XSLT à partir de l’éditeur XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).  
  
 **Débogage XSLT**  
 Vous pouvez lancer le débogueur XSLT à partir d'un fichier XSLT dans l'éditeur XML. Le débogueur prend en charge la définition de points d'arrêt dans le fichier XSLT, l'affichage de l'état d'exécution de XSLT, etc. Lorsque le pointeur est placé sur une variable XSLT, une info-bulle apparaît et affiche la valeur de la variable. Le débogueur peut permettre de déboguer une feuille de style ou une transformation XSLT compilée invoquée depuis une autre application. Pour plus d’informations, consultez [XSLT débogage](../xml-tools/debugging-xslt.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)
