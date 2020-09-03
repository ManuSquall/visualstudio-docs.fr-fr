---
title: Restrictions sur les longueurs de chaîne | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df6e068ba612d5e8876e4fa01fbc0751759d5a80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701474"
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
