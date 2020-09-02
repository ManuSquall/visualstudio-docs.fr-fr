---
title: Attributs de prise en charge de site Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144310"
---
# <a name="web-site-support-attributes"></a>Attributs de prise en charge de site web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Le projet de site Web peut être étendu pour assurer la prise en charge des langages de programmation Web. La langue doit s’inscrire auprès de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] afin que les modèles de projet puissent apparaître dans la boîte de dialogue **nouveau site Web** lorsque la langue est sélectionnée.  
  
 L’exemple IronPython Studio comprend la prise en charge des sites Web. Vous pouvez le trouver avec les [exemples VSSDK](../../misc/vssdk-samples.md). Il comprend les classes d’attributs suivantes pour inscrire IronPython comme langage codebehind pour les nouveaux projets Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Cet attribut est placé sur le projet de langage. Elle ajoute la langue à la liste des langages de programmation Web dans la liste **langue** de la boîte de dialogue **nouveau site Web** . Par exemple, l’exemple suivant ajoute IronPython à la liste :  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Cet attribut définit également le chemin d’accès des modèles pour qu’il pointe vers le dossier Templates. Pour plus d’informations sur l’emplacement du dossier de modèles, consultez [modèles de prise en charge de site Web](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Cet attribut est placé sur le projet de langage. Elle permet au projet de site Web d’imbriquer un type de fichier (associé) sous un autre type de fichier (principal) dans le **Explorateur de solutions**.  
  
 Par exemple :  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Spécifie qu’un fichier codebehind IronPython est associé à un fichier. aspx. Quand une nouvelle page Web. aspx est créée dans une solution de site Web IronPython, un nouveau fichier source. py est généré et apparaît en tant que nœud enfant de la page. aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Cet attribut est placé sur le package de projet de langage. Il sélectionne le fournisseur IntelliSense pour le langage.  
  
 Par exemple :  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Spécifie qu’une instance de PythonIntellisenseProvider, qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , doit être créée à la demande pour fournir des services de langage.  
  
 L’implémentation IVsIntellisenseProject gère les références et appelle le compilateur de langage lorsqu’une page Web avec du code est demandée mais n’est pas mise en cache.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de site web](../../extensibility/internals/web-site-support.md)
