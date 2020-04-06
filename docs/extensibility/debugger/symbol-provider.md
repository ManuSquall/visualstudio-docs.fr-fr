---
title: Fournisseur de symboles (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712818"
---
# <a name="symbol-provider"></a>Fournisseur de symboles
Une mise en œuvre d’évaluateur d’expression doit accéder aux informations symboliques de débagé générées par le compilateur linguistique afin d’évaluer les variables et les expressions. Il le fait en consommant les interfaces d’un fournisseur de symboles (SP), également appelé un gestionnaire de symbole.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fournit des SPs pour le code géré ainsi que le code natif à l’aide du format de fichier symbole Program DataBase (PDB). À moins qu’il n’y ait un fort besoin pour votre programme d’utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]des symboles stockés dans un format personnalisé, il est recommandé que vous utilisiez les SPs fournis par .

## <a name="implementation-notes"></a>Remarques relatives à l’implémentation
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moteurs de déboguer s’attendent à parler avec les SPs en utilisant les interfaces Common Language Runtime (CLR). En conséquence, un SP qui travaillera avec les moteurs de déboiffés Visual Studio doit prendre en charge le CLR. Une liste complète de toutes les interfaces de débogage CLR peut être [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]trouvé dans debugref.doc, qui fait partie de la .

 Si votre SP ne fonctionne qu’avec votre moteur de débogé personnalisé, vous pouvez implémenter le SP comme bon vous semble en fonction des besoins de votre moteur de débogé.

## <a name="see-also"></a>Voir aussi
- [Composants Debugger](../../extensibility/debugger/debugger-components.md)
