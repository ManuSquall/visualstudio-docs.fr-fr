---
title: Erreurs et avertissements XAML
description: En savoir plus sur les erreurs et avertissements XAML dans Visual Studio, notamment sur la façon dont les erreurs sont catégorisées, sur l’obtention d’informations sur les erreurs et sur la façon de trouver des options pour les corriger.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a68273f4fbb2f66986c18c692b91b6e1829a4c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049214"
---
# <a name="xaml-errors-and-warnings"></a>Erreurs et avertissements XAML

Lors de la création de XAML, Visual Studio analyse le code au fur et à mesure de la saisie. Une ligne ondulée apparaît sur une ligne de code lorsqu’une erreur est détectée. Placez le curseur sur la ligne ondulée pour avoir plus d’informations sur l’erreur ou l’avertissement. Pour des erreurs et des avertissements, une ampoule d’action rapide s’affiche et utilise la **touche Ctrl** + **.** permet d’afficher les options qui permettront de résoudre le problème.

## <a name="error-types"></a>Types d’erreurs

Dans les coulisses, plusieurs outils analysent le code XAML en parallèle. Les erreurs XAML sont classées dans l’une des trois catégories suivantes, en fonction de l’outil qui a détecté l’erreur :

|**Erreur détectée par**|**Format de code d’erreur**|**Version de Visual Studio**|
| - |-----------------| - |
|Service de langage XAML (éditeur XAML)|XLSxxxx| Toutes les versions |
|Concepteur XAML|XDGxxxx| Toutes les versions | 
|Modifier & Continuer pour le code XAML|XECxxxx| Visual Studio 2019 version 16,1 ou antérieure |
|Rechargement à chaud XAML | XHRxxxx | Visual Studio 2019 version 16,2 ou ultérieure |

Pour plus d’informations sur la repersonnalisation de la modification XAML & continuer en tant que rechargement à chaud XAML, consultez nos [notes de publication](https://docs.microsoft.com/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling)

> [!Note]
> Les erreurs ou avertissements n’ont pas tous un code correspondant. Ces erreurs sont généralement des erreurs du concepteur XAML.

## <a name="suppress-xaml-designer-errors"></a>Supprimer les erreurs du concepteur XAML

Ouvrez la boîte de dialogue **Options** en sélectionnant **Outils > Options** , puis sélectionnez **Éditeur de texte > XAML > Divers** .

Désactivez la case à cocher **Afficher les erreurs détectées par le concepteur XAML** .

![Supprimer les erreurs du concepteur XAML](media/suppress_xaml_designer_errors.png)
