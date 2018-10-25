---
title: Prise en charge d’Automation pour les Pages Options | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b18f8df30dc9f3385c2c5f154d66c598b423968e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929645"
---
# <a name="automation-support-for-options-pages"></a>Automation prend en charge pour les pages Options
VSPackages peut fournir une personnalisée **Options** boîtes de dialogue pour le **outils** menu (**Outils/Options** pages) dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et vous pouvez les rendre disponibles pour l’automatisation modèle.  
  
## <a name="tools-options-pages"></a>pages d'options Outils  
 Pour créer un **Outils/Options** page, un VSPackage doit fournir une implémentation de contrôle utilisateur retournée à l’environnement via l’implémentation du VSPackage de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (méthode). (Ou, pour le code managé, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (méthode).) 
  
 Il est facultatif, mais il est vivement recommandé d’autoriser l’accès à cette nouvelle page via le modèle automation. Vous pouvez le faire en procédant comme suit :  
  
1. Étendre la <xref:EnvDTE._DTE.Properties%2A> objet via l’implémentation d’un objet dérivé de IDispatch.  
  
2. Retourner une implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (méthode) (ou pour le code managé le <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> méthode) à l’objet dérivé de IDispatch.  
  
3. Lorsqu’un utilisateur d’automation appelle le <xref:EnvDTE._DTE.Properties%2A> méthode sur un personnalisé **Option** page de propriétés, l’environnement utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode pour obtenir un personnalisé **Outils/Options** automation de la page mise en œuvre.  
  
4. L’objet automation du VSPackage est ensuite utilisé pour fournir chacune <xref:EnvDTE.Property> retourné par <xref:EnvDTE._DTE.Properties%2A>.  
  
   Pour obtenir un exemple d’implémentation personnalisé **Outils/Options** page, consultez [exemples d’extensibilité Visual Studio](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Voir aussi  
 [Exposer des objets du projet](../../extensibility/internals/exposing-project-objects.md)