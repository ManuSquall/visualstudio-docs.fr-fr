---
title: Automatisation pour la configuration et les objets SélectionnésItem Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709973"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisation pour les objets Configuration et SelectedItem

Vous pouvez automatiser les processus de construction et d’objets sélectionnés dans Visual Studio.

## <a name="automation-for-builds"></a>Automatisation pour les constructions

Construire ou configuration a un modèle d’automatisation qui est fourni lorsque vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Pour plus d’informations, consultez [Présentation des configurations de build](../../ide/understanding-build-configurations.md).

Si vous créez un VSPackage et souhaitez contrôler les options de configuration, vous devez utiliser le modèle d’automatisation.

## <a name="automation-for-selecteditem"></a>Automatisation pour SelectedItem

Vous n’avez pas à `SelectedItem` fournir une implémentation pour l’objet parce que Visual Studio contient une implémentation standard. Cependant, vous pouvez `SelectedItem` implémenter l’objet si vous préférez. Vous devez implémenter `SelectedItem` un objet qui contient l’interface et retourner une réponse à un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode avec `VSITEMID` défini à [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuer au modèle d’automatisation](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Présentation des configurations de build](../../ide/understanding-build-configurations.md)
