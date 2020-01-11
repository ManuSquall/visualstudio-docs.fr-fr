---
title: Prise en charge d’Automation pour les pages d’options | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03360bfc01110e7b4ef73956f0199aaaed9cee2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848968"
---
# <a name="automation-support-for-options-pages"></a>Prise en charge d’Automation pour les pages d’options
Les VSPackages peuvent fournir des boîtes de dialogue **options** personnalisées au menu **Outils** (pages**Options des outils** ) dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et peuvent les mettre à la disposition du modèle Automation.

## <a name="tools-options-pages"></a>pages d'options Outils
 Pour créer une page **Outils Options** , un VSPackage doit fournir une implémentation de contrôle utilisateur retournée à l’environnement par le biais de l’implémentation du VSPackage de la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>. (Ou, pour le code managé, la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>.)

 C’est facultatif, mais vivement encouragé, pour autoriser l’accès à cette nouvelle page via le modèle Automation. Pour ce faire, procédez comme suit :

1. Étendez l’objet <xref:EnvDTE._DTE.Properties%2A> par le biais de l’implémentation d’un objet dérivé de IDispatch.

2. Retournez une implémentation de la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (ou du code managé de la méthode <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>) à l’objet dérivé de IDispatch.

3. Lorsqu’un consommateur Automation appelle la méthode <xref:EnvDTE._DTE.Properties%2A> sur une page de propriétés **option** personnalisée, l’environnement utilise la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> pour obtenir une implémentation Automation de la page **Options des outils** personnalisés.

4. L’objet Automation du VSPackage est ensuite utilisé pour fournir chaque <xref:EnvDTE.Property> retourné par <xref:EnvDTE._DTE.Properties%2A>.

   Pour obtenir un exemple d’implémentation d’une page **Outils/Options** personnalisée, consultez [exemples VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Voir aussi
- [Exposer des objets de projet](../../extensibility/internals/exposing-project-objects.md)
