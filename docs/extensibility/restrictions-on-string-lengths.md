---
title: Restrictions relatives aux longueurs de chaîne | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab797f76ec6f6118fe4f86a410dbfcfe1e61aa04
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334174"
---
# <a name="restrictions-on-string-lengths"></a>Restrictions relatives aux longueurs de chaîne
L’API de plug-in de contrôle de Source de limite les longueurs des chaînes utilisées dans les différentes fonctions.

## <a name="string-length-values"></a>Valeurs de longueur de chaîne

|Constante|Value|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> Longueur n’inclut pas la fin `null`. Autres constantes avec un suffixe « _Taille » au lieu de « _LEN » n’incluent pas d’espace pour le point final `null`.

|Constante|Value|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)