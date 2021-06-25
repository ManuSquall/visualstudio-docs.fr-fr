---
title: Restrictions sur les longueurs de chaîne | Microsoft Docs
description: En savoir plus sur les limites des longueurs de chaînes utilisées par les différentes fonctions imposées par l’API de plug-in de contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7fd0d88a50f64aee1f0bc5c273d7a3cd50c6f53f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900250"
---
# <a name="restrictions-on-string-lengths"></a>Restrictions sur les longueurs de chaîne
L’API de plug-in de contrôle de code source limite les longueurs de chaînes utilisées dans différentes fonctions.

## <a name="string-length-values"></a>Valeurs de longueur de chaîne

|Constante|Valeur|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> La longueur n’inclut pas l’arrêt `null` . Les autres constantes avec un suffixe « _SIZE » au lieu de « _LEN » incluent de l’espace pour l’arrêt `null` .

|Constante|Valeur|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
