---
title: Erreurs et avertissements XAML
ms.date: 03/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09251f13cafa320e2736e9c61135283bb9e9739d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844183"
---
# <a name="xaml-errors-and-warnings"></a>Erreurs et avertissements XAML

Lors de la création de XAML, Visual Studio analyse le code au fur et à mesure de la saisie. Une ligne ondulée apparaît sur une ligne de code lorsqu’une erreur est détectée. Placez le curseur sur la ligne ondulée pour avoir plus d’informations sur l’erreur ou l’avertissement. Pour certains types d’erreurs et d’avertissements, une ampoule Action rapide s’affiche, et le raccourci clavier **Ctrl**+**.** permet d’afficher les options qui permettront de résoudre le problème.

## <a name="error-types"></a>Types d’erreurs

Dans les coulisses, plusieurs outils analysent le code XAML en parallèle. Les erreurs XAML sont classées dans l’une des trois catégories suivantes, en fonction de l’outil qui a détecté l’erreur :

|**Erreur détectée par**|**Format de code d’erreur**|
| - |-----------------|
|Service de langage XAML (éditeur XAML)|XLSxxxx|
|Concepteur XAML|XDGxxxx|
|Modifier et continuer XAML|XECxxxx|

> [!Note]
> Les erreurs ou avertissements n’ont pas tous un code correspondant. Ces erreurs sont généralement des erreurs du concepteur XAML.


## <a name="suppress-xaml-designer-errors"></a>Supprimer les erreurs du concepteur XAML

Ouvrez la boîte de dialogue **Options** en sélectionnant **Outils > Options**, puis sélectionnez **Éditeur de texte > XAML > Divers**.

Désactivez la case à cocher **Afficher les erreurs détectées par le concepteur XAML**.

![Supprimer les erreurs du concepteur XAML](../designers/media/suppress_xaml_designer_errors.png)


