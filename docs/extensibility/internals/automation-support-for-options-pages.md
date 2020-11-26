---
title: Prise en charge d’Automation pour les pages d’options | Microsoft Docs
description: Découvrez comment rendre disponibles les pages d’options Outils personnalisées dans les VSPackages dans le modèle Automation de Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1e15b1f8bdd27e013e1ef2060d9867a81e8ddde3
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190029"
---
# <a name="automation-support-for-options-pages"></a>Prise en charge d’Automation pour les pages d’options
Les VSPackages peuvent fournir des boîtes de dialogue **options** personnalisées au menu **Outils** (pages **Options des outils** ) dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et peuvent les mettre à la disposition du modèle Automation.

## <a name="tools-options-pages"></a>pages d'options Outils
 Pour créer une page **Outils Options** , un VSPackage doit fournir une implémentation de contrôle utilisateur retournée à l’environnement par le biais de l’implémentation du VSPackage de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode. (Ou, pour le code managé, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode.)

 C’est facultatif, mais vivement encouragé, pour autoriser l’accès à cette nouvelle page via le modèle Automation. Pour cela, effectuez les étapes ci-dessous :

1. Étendez l' <xref:EnvDTE._DTE.Properties%2A> objet via l’implémentation d’un objet dérivé de IDispatch.

2. Retournez une implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode (ou du code managé de la <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> méthode) à l’objet dérivé de IDispatch.

3. Lorsqu’un consommateur Automation appelle la <xref:EnvDTE._DTE.Properties%2A> méthode sur une page de propriétés d' **option** personnalisée, l’environnement utilise la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode pour obtenir une implémentation Automation de la page **Options des outils** personnalisés.

4. L’objet Automation du VSPackage est ensuite utilisé pour fournir chaque <xref:EnvDTE.Property> retourné par <xref:EnvDTE._DTE.Properties%2A> .

   Pour obtenir un exemple d’implémentation d’une page **Outils/Options** personnalisée, consultez [exemples VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Voir aussi
- [Exposer des objets de projet](../../extensibility/internals/exposing-project-objects.md)
