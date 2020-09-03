---
title: Automatisation pour la configuration et les objets SelectedItem | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709973"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisation pour la configuration et les objets SelectedItem

Vous pouvez automatiser les processus de génération et d’élément sélectionné dans Visual Studio.

## <a name="automation-for-builds"></a>Automation pour les builds

La génération ou la configuration dispose d’un modèle Automation qui est fourni quand vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Pour plus d’informations, consultez [Présentation des configurations de build](../../ide/understanding-build-configurations.md).

Si vous créez un VSPackage et souhaitez contrôler les options de configuration, vous devez utiliser le modèle Automation.

## <a name="automation-for-selecteditem"></a>Automatisation pour SelectedItem

Vous n’avez pas besoin de fournir une implémentation pour l' `SelectedItem` objet, car Visual Studio contient une implémentation standard. Toutefois, vous pouvez implémenter l' `SelectedItem` objet si vous préférez. Vous devez implémenter un objet qui contient l' `SelectedItem` interface et retourner une réponse à un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode avec la `VSITEMID` valeur [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuer au modèle Automation](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Présentation des configurations de build](../../ide/understanding-build-configurations.md)
