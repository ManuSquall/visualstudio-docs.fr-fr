---
title: Modification des feuilles de Style XSLT | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bc7cb28171711de757708b80f6a2745c1187151b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501416"
---
# <a name="editing-xslt-style-sheets"></a>Modification de feuilles de style XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [modification des feuilles de Style XSLT](https://docs.microsoft.com/visualstudio/xml-tools/editing-xslt-style-sheets).  
  
  
L'Éditeur XML permet également de modifier des feuilles de style XSLT. Vous pouvez ainsi tirer profit des fonctionnalités par défaut de l'éditeur telles qu'IntelliSense, mode plan, extraits XML, etc. Des nouvelles fonctions facilitent en outre le développement en XSLT.  
  
## <a name="xslt-features"></a>Fonctions XSLT  
 Le tableau suivant décrit les fonctionnalités spécifiques à la manipulation des feuilles de style XSLT.  
  
 **La coloration syntaxique**  
 Mots clés XSLT, tels que `template`, `match`, et ainsi de suite, sont affichés dans la couleur de mot clé XSLT spécifiée par le **polices et couleurs** paramètres.  
  
 **Soulignements ondulés**  
 L'éditeur XML utilise le fichier installé xslt.xsd pour valider les feuilles de style XSLT. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. L'éditeur XML compile également la feuille de style en arrière-plan et signale les erreurs ou avertissements du compilateur à l'aide de soulignements ondulés appropriés.  
  
 **Prise en charge des blocs de script**  
 Le code placé dans des blocs de script est pris en charge par le débogueur XSLT ; vous pouvez donc définir des points d'arrêt et effectuer une exécution pas à pas dans le code du bloc de script.  
  
 **Afficher la sortie XSLT**  
 Vous pouvez exécuter une transformation XSL et afficher la sortie depuis l'éditeur XML. Pour plus d’informations, consultez [Comment : exécuter une Transformation XSLT à partir de l’éditeur XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).  
  
 **Débogage XSLT**  
 Vous pouvez lancer le débogueur XSLT à partir d'un fichier XSLT dans l'éditeur XML. Le débogueur prend en charge la définition de points d'arrêt dans le fichier XSLT, l'affichage de l'état d'exécution de XSLT, etc. Lorsque le pointeur est placé sur une variable XSLT, une info-bulle apparaît et affiche la valeur de la variable. Le débogueur peut permettre de déboguer une feuille de style ou une transformation XSLT compilée invoquée depuis une autre application. Pour plus d’informations, consultez [XSLT débogage](../xml-tools/debugging-xslt.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)



