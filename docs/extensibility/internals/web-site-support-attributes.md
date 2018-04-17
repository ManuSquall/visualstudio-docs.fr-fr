---
title: Attributs de prise en charge du Site Web | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b312322c1d707f13c5121f1fd159f3fd7736886c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="web-site-support-attributes"></a>Attributs de prise en charge de Site Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projet de site Web peut être étendu pour prendre en charge pour le Web de langages de programmation. La langue doit s’inscrire avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] afin que les modèles de projet s’affiche dans le **nouveau Site Web** boîte de dialogue lorsque la langue est sélectionnée.

L’exemple IronPython Studio inclut la prise en charge du site web. L’exemple contient les classes d’attribut suivantes pour inscrire IronPython comme langage de code-behind pour les nouveaux projets Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Cet attribut est placé sur le projet de langage. Il ajoute la langue à la liste des langages de programmation Web les **langage** liste dans le **nouveau Site Web** boîte de dialogue. Par exemple, le code suivant ajoute IronPython à la liste :

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Cet attribut définit également le chemin d’accès de modèles pour pointer vers le dossier des modèles. Pour plus d’informations sur l’emplacement du dossier de modèles, consultez [modèles de prise en charge des sites Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Cet attribut est placé sur le projet de langage. Il permet le projet de Site Web d’imbriquer un type de fichier (lié) sous un autre type de fichier (principal) dans le **l’Explorateur de solutions**.

 Par exemple, le code suivant spécifie qu’un fichier de code-behind IronPython est lié à un fichier .aspx. Lorsqu’une page Web .aspx est créée dans une solution de site Web de IronPython, un nouveau fichier de source .py est généré et apparaît sous la forme d’un nœud enfant de la page .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Cet attribut est placé sur le package de projet de langage. Il sélectionne le fournisseur d’IntelliSense pour la langue.

 Par exemple, le code suivant spécifie qu’une instance de PythonIntellisenseProvider, qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, doit être créé à la demande pour fournir des services de langage.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 L’implémentation de IVsIntellisenseProject traite les références et appelle le compilateur de langage lorsqu’une page Web avec le code est demandée mais n’est pas mis en cache.

## <a name="see-also"></a>Voir aussi
 [Prise en charge de site Web](../../extensibility/internals/web-site-support.md)