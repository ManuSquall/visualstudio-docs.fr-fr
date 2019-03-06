---
title: Attributs de prise en charge de Site Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 076b7aa56ec00fda559bbdfdc8b2b9df2be38816
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603129"
---
# <a name="web-site-support-attributes"></a>Attributs de prise en charge de site web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projet de site Web peut être étendu pour prendre en charge pour le Web, langages de programmation. La langue doit s’inscrire avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] afin que les modèles de projet peuvent apparaître dans le **nouveau Site Web** boîte de dialogue lors de la langue sélectionnée.

L’exemple de IronPython Studio inclut la prise en charge du site web. L’exemple contient des classes d’attributs suivantes pour inscrire IronPython comme un langage de code-behind pour les nouveaux projets Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Cet attribut est placé sur le projet de langage. Il ajoute la langue à la liste des langages de programmation Web le **langage** liste dans le **nouveau Site Web** boîte de dialogue. Par exemple, le code suivant ajoute IronPython à la liste :

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Cet attribut définit également le chemin d’accès de modèles pour pointer vers le dossier de modèles. Pour plus d’informations sur l’emplacement du dossier de modèles, consultez [modèles de prise en charge de Site Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Cet attribut est placé sur le projet de langage. Il permet au projet de Site Web d’imbriquer un type de fichier (associé) sous un autre type de fichier (principal) dans le **l’Explorateur de solutions**.

 Par exemple, le code suivant spécifie qu’un fichier de code-behind IronPython est lié à un fichier .aspx. Création d’une page Web .aspx dans une solution de site Web de IronPython, un nouveau fichier de source .py est généré et apparaît sous la forme d’un nœud enfant de la page .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Cet attribut est placé sur le package de projet de langage. Il sélectionne le fournisseur d’IntelliSense pour la langue.

 Par exemple, le code suivant spécifie qu’une instance de PythonIntellisenseProvider, qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, doit être créée à la demande pour fournir des services de langage.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 L’implémentation de IVsIntellisenseProject traite les références et appelle le compilateur de langage lorsqu’une page Web avec le code est demandée mais n’est pas mis en cache.

## <a name="see-also"></a>Voir aussi
- [Prise en charge de site Web](../../extensibility/internals/web-site-support.md)