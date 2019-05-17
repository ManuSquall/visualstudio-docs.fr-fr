---
title: FxCopCmd (erreurs) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3e0770654f564c57cf576666dcd9575f47d9ce1c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432292"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd (erreurs)
FxCopCmd ne considère pas toutes les erreurs comme irrécupérable. Si FxCopCmd dispose d’informations suffisantes pour effectuer une analyse partielle, il effectue l’analyse et signale les erreurs qui se sont produites. Le code d’erreur, qui est un entier 32 bits, contient une combinaison au niveau du bit des valeurs numériques qui correspondent aux erreurs.  
  
 Le tableau suivant décrit les codes d’erreur retournés par FxCopCmd :  
  
|Error|Valeur numérique|  
|-----------|-------------------|  
|Aucune erreur|0x0|  
|Erreur d’analyse|0x1|  
|Exceptions de règle|0x2|  
|Erreur de chargement de projet|0x4|  
|Erreur de chargement d’assembly|0x8|  
|Erreur de chargement de bibliothèque de règle|0x10|  
|Erreur de chargement du rapport importation|0x20|  
|Erreur de sortie|0x40|  
|Erreur de commutateur de ligne de commande|0x80|  
|Erreur d’initialisation|0x100|  
|Erreur des références d’assembly|0x200|  
|BuildBreakingMessage|0 x 400|  
|Erreur inconnue|0x1000000|  
  
 L’erreur d’analyse est retournée pour les erreurs irrécupérables. Il indique que l’analyse a échoué. Le cas échéant, le code d’erreur contient également la cause sous-jacente de l’erreur irrécupérable. Les conditions suivantes génèrent des erreurs irrécupérables :  
  
- L’analyse n’a pas pu être effectuée provoquée par l’entrée insuffisante.  
  
- L’analyse a levé une exception non gérée par FxCopCmd.  
  
- Le fichier projet spécifié est introuvable ou est endommagé.  
  
- L’option de sortie n’a pas été spécifiée ou le fichier n’a pas pu être écrites.  
  
    > [!NOTE]
    > Le code retour FxCopCmd « Erreur des références d’Assembly » 0 x 200 en lui-même est un avertissement plutôt qu’une erreur. Ce code de retour indique que des références indirectes manquantes ont été trouvés, mais que FxCopCmd a été en mesure de les gérer. Il s’agit d’un avertissement qu’il est possible que certains résultats de l’analyse a été compromises. Envisagez le code de retour « Erreur des références d’Assembly » comme une erreur lorsqu’il est combiné avec n’importe quel autre code de retour.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)