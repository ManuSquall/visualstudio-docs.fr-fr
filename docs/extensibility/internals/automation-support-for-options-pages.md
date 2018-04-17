---
title: Prise en charge d’Automation pour les Pages d’Options | Documents Microsoft
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
ms.openlocfilehash: d27ad706d4203a3573a734a1cd11b19e3c9df6a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="automation-support-for-options-pages"></a>Prise en charge d’Automation pour les Pages d’Options
VSPackages peuvent fournir personnalisée **Options** boîtes de dialogue pour le **outils** menu (pages Outils Options) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et vous pouvez les rendre disponibles pour le modèle automation.  
  
## <a name="tools-options-pages"></a>Pages Outils Options  
 Pour créer un **Outils Options** page, un VSPackage doit fournir une implémentation du contrôle utilisateur retournée à l’environnement via l’implémentation du VSPackage de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (méthode), (ou pour le code managé du <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode).  
  
 Il est facultatif, mais il est vivement recommandé d’autoriser l’accès à cette nouvelle page via le modèle automation. Pour cela, les étapes suivantes :  
  
1.  Étendre la <xref:EnvDTE._DTE.Properties%2A> objet via l’implémentation d’un objet dérivé de IDispatch.  
  
2.  Retourner une implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (méthode) (ou pour le code managé la <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> méthode) à l’objet dérivée de IDispatch.  
  
3.  Lorsqu’un client automation appelle la <xref:EnvDTE._DTE.Properties%2A> méthode sur une personnalisée **Option** page de propriétés, l’environnement utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode pour obtenir une personnalisée **Outils Options** automation de la page mise en œuvre.  
  
4.  L’objet automation du VSPackage sert ensuite à fournir chacun <xref:EnvDTE.Property> retourné par <xref:EnvDTE._DTE.Properties%2A>.  
  
 Pour obtenir un exemple d’implémentation d’une page d’Options des outils personnalisée, consultez [exemples d’extensibilité Visual Studio](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Voir aussi  
 [Exposition des objets de projet](../../extensibility/internals/exposing-project-objects.md)