---
title: Prise en charge d’Automation pour les pages d’options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157247"
---
# <a name="automation-support-for-options-pages"></a>Prise en charge de l’automatisation pour les pages Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les VSPackages peuvent fournir des boîtes de dialogue **options** personnalisées au menu **Outils** (pages Options des outils) dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et peuvent les mettre à la disposition du modèle Automation.  
  
## <a name="tools-options-pages"></a>Pages d’options des outils  
 Pour créer une page **Outils Options** , un VSPackage doit fournir une implémentation de contrôle utilisateur retournée à l’environnement par le biais de l’implémentation du VSPackage de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode (ou pour le code managé de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode).  
  
 Il est facultatif, mais vivement encouragé, d’autoriser l’accès à cette nouvelle page via le modèle Automation. Pour ce faire, procédez comme suit :  
  
1. Étendez l' <xref:EnvDTE._DTE.Properties%2A> objet via l’implémentation d’un objet dérivé de IDispatch.  
  
2. Retournez une implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode (ou du code managé de la <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> méthode) à l’objet dérivé de IDispatch.  
  
3. Lorsqu’un consommateur Automation appelle la <xref:EnvDTE._DTE.Properties%2A> méthode sur une page de propriétés d' **option** personnalisée, l’environnement utilise la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode pour obtenir une implémentation Automation de la page **Options des outils** personnalisés.  
  
4. L’objet Automation du VSPackage est ensuite utilisé pour fournir chaque <xref:EnvDTE.Property> retourné par <xref:EnvDTE._DTE.Properties%2A> .  
  
   Pour obtenir un exemple d’implémentation d’une page outils/options personnalisée, consultez [exemples VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exposition des objets de projet](../../extensibility/internals/exposing-project-objects.md)
