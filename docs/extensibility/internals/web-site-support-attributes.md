---
title: Attributs de prise en charge de site Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07486ea3a962bcb81f65ad0b61ea2e41b3248678
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721612"
---
# <a name="web-site-support-attributes"></a>Attributs de prise en charge de site web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet de site Web peut être étendu pour assurer la prise en charge des langages de programmation Web. La langue doit s’inscrire auprès de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] afin que les modèles de projet puissent apparaître dans la boîte de dialogue **nouveau site Web** lorsque la langue est sélectionnée.

L’exemple IronPython Studio comprend la prise en charge des sites Web. L’exemple contient les classes d’attributs suivantes pour inscrire IronPython comme langage codebehind pour les nouveaux projets Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Cet attribut est placé sur le projet de langage. Elle ajoute la langue à la liste des langages de programmation Web dans la liste **langue** de la boîte de dialogue **nouveau site Web** . Par exemple, le code suivant ajoute IronPython à la liste :

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Cet attribut définit également le chemin d’accès des modèles pour qu’il pointe vers le dossier Templates. Pour plus d’informations sur l’emplacement du dossier de modèles, consultez [modèles de prise en charge de site Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Cet attribut est placé sur le projet de langage. Elle permet au projet de site Web d’imbriquer un type de fichier (associé) sous un autre type de fichier (principal) dans le **Explorateur de solutions**.

 Par exemple, le code suivant spécifie qu’un fichier codebehind IronPython est associé à un fichier. aspx. Quand une nouvelle page Web. aspx est créée dans une solution de site Web IronPython, un nouveau fichier source. py est généré et apparaît en tant que nœud enfant de la page. aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Cet attribut est placé sur le package de projet de langage. Il sélectionne le fournisseur IntelliSense pour le langage.

 Par exemple, le code suivant spécifie qu’une instance de PythonIntellisenseProvider, qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, doit être créée à la demande pour fournir des services de langage.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 L’implémentation IVsIntellisenseProject gère les références et appelle le compilateur de langage lorsqu’une page Web avec du code est demandée mais n’est pas mise en cache.

## <a name="see-also"></a>Voir aussi
- [Prise en charge de site Web](../../extensibility/internals/web-site-support.md)