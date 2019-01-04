---
title: Concepteur de flux de travail - ajouter des paramètres et ajouter des boîtes de dialogue d’Arguments
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- AddParameters.UI
ms.assetid: a21fb4fe-134b-40b0-8497-86b842940ca1
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f0a9868566ad77441d31929acc2d6fddb1736eb2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823867"
---
# <a name="add-parameters-and-add-arguments-dialog-boxes"></a>Boîtes de dialogue Ajouter des paramètres et Ajouter des arguments

Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **ajouter des paramètres** boîte de dialogue utilisée par le <xref:System.Activities.Statements.InvokeMethod> concepteur :

|||
|-|-|
|**Direction**|Spécifie si le paramètre représente le flux de données dans la méthode, hors de la méthode, ou les deux.|
|**Type**|Nom du type du nouveau paramètre.|
|**Valeur**|Une expression Visual Basic qui est utilisée pour affecter une valeur par défaut pour le nouveau paramètre|

Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **ajouter des Arguments** boîte de dialogue utilisée par le <xref:System.Activities.Statements.InvokeDelegate> concepteur :

|||
|-|-|
|**Name**|Nom de l’argument.|
|**Direction**|Spécifie si l’argument représente le flux de données dans le délégué, hors du délégué, ou les deux.|
|**Type**|Nom du type du nouvel argument.|
|**Valeur**|Valeur à utiliser pour cette instance de l’argument de délégué.|