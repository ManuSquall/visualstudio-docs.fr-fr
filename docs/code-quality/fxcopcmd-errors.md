---
title: FxCopCmd (erreurs) | Documents Microsoft
ms.date: 10/19/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b407167a772a82b56c39ba222dc3c1f563f5c012
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd (erreurs) outil

FxCopCmd ne tient pas compte de toutes les erreurs comme irrécupérable. Si FxCopCmd dispose d’informations suffisantes pour effectuer une analyse partielle, il effectue l’analyse et signale les erreurs qui se sont produites. Le code d’erreur, qui est un entier 32 bits, contient une combinaison d’opérations de bits de valeurs numériques qui correspondent à des erreurs.

Le tableau suivant décrit les codes d’erreur retournés par FxCopCmd :

|Error|Valeur numérique|
|-----------|-------------------|
|Pas d’erreurs|0x0|
|Erreur d’analyse|0x1|
|Exceptions de règle|0x2|
|Erreur de chargement du projet|0x4|
|Erreur de chargement d’assembly|0x8|
|Erreur de chargement de bibliothèque de règle|0x10|
|Erreur de chargement du rapport importation|0x20|
|Erreur de sortie|0x40|
|Erreur de commutateur de ligne de commande|0x80|
|Erreur d’initialisation|0x100|
|Erreur des références d’assembly|0x200|
|BuildBreakingMessage|0x400|
|Erreur inconnue|0x1000000|

**Erreur d’analyse** est renvoyée pour les erreurs irrécupérables. Il indique que l’analyse a échoué. Le cas échéant, le code d’erreur contient également la cause sous-jacente de l’erreur irrécupérable. Les conditions suivantes génèrent des erreurs irrécupérables :

- L’analyse n’a pas pu être effectuée en raison d’une entrée insuffisante.

- L’analyse a levé une exception non gérée par FxCopCmd.

- Le fichier projet spécifié est introuvable ou est endommagé.

- L’option de sortie n’a pas été spécifiée ou le fichier n’a pas pu être écrit.

> [!NOTE]
> Le code retour FxCopCmd **erreur des références d’Assembly** 0 x 200 seul est un avertissement plutôt qu’erreur. Ce code de retour indique qu’il manque des références indirectes, mais que FxCopCmd a été en mesure de les gérer. L’avertissement signifie que, il est possible que certains résultats de l’analyse a été compromises. Traiter **erreur des références d’Assembly** comme une erreur lorsqu’il est combiné avec tout autre code de retour.

## <a name="see-also"></a>Voir aussi

- [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)