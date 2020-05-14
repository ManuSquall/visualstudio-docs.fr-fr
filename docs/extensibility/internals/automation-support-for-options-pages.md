---
title: Support d’automatisation pour les pages d’options (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709929"
---
# <a name="automation-support-for-options-pages"></a>Support d’automatisation pour les pages Options
VSPackages peut fournir des boîtes de dialogue **Options** personnalisées [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] au menu **Tools** **(pages Options Outils)** et peut les mettre à la disposition du modèle d’automatisation.

## <a name="tools-options-pages"></a>pages d'options Outils
 Pour créer une page **Options d’outils,** un VSPackage doit fournir une implémentation <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> de contrôle utilisateur retournée dans l’environnement grâce à la mise en œuvre de la méthode par LE VSPackage. (Ou, pour le code <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> géré, la méthode.)

 Il est facultatif, mais fortement encouragé, pour permettre l’accès à cette nouvelle page à travers le modèle d’automatisation. Vous pouvez le faire avec les étapes suivantes :

1. Étendre <xref:EnvDTE._DTE.Properties%2A> l’objet par la mise en œuvre d’un objet dérivé de l’IDispatch.

2. Retournez une <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> implémentation de <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> la méthode (ou pour le code géré de la méthode) à l’objet dérivé de l’IDispatch.

3. Lorsqu’un consommateur <xref:EnvDTE._DTE.Properties%2A> d’automatisation appelle la méthode sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> une page de propriété **Option** personnalisée, l’environnement utilise la méthode pour obtenir la mise en œuvre d’automatisation d’une page **Tools Options** personnalisée.

4. L’objet d’automatisation du VSPackage <xref:EnvDTE.Property> est <xref:EnvDTE._DTE.Properties%2A>ensuite utilisé pour fournir chaque retour par .

   Pour un exemple de mise en œuvre d’une page **Options d’outils** personnalisées, voir [échantillons VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Voir aussi
- [Exposer les objets du projet](../../extensibility/internals/exposing-project-objects.md)
