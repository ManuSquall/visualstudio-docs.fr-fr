---
title: Restrictions relatives aux longueurs de chaîne | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ade5e9ac188cd6c1b721ed276e0c4e2aff71f32
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434713"
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