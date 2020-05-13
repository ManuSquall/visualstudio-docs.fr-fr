---
title: Attributs de support de site Web Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703496"
---
# <a name="web-site-support-attributes"></a>Attributs de prise en charge de site web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Le projet de site Web peut être étendu pour fournir un soutien aux langages de programmation Web. La langue doit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s’inscrire avec de sorte que les modèles de projet peuvent apparaître dans la boîte de dialogue **du nouveau site Web** lorsque la langue est sélectionnée.

L’échantillon d’IronPython Studio comprend le support du site Web. L’échantillon contient les classes d’attributs suivantes pour enregistrer IronPython comme langue codébehind pour de nouveaux projets Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Cet attribut est placé sur le projet linguistique. Il ajoute la langue à la liste des langages de programmation Web dans la liste **linguistique** dans la boîte de dialogue **du nouveau site Web.** Par exemple, le code suivant ajoute IronPython à la liste :

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Cet attribut définit également le chemin des modèles pour pointer vers le dossier de modèles. Pour plus d’informations sur l’emplacement du dossier de modèles, voir [modèles de support de site Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute WebSiteProjectRelatedFilesAttribute WebSiteProjectRelatedFilesAttribute WebS
 Cet attribut est placé sur le projet linguistique. Il permet au projet de site Web de nicher un type de fichier (connexe) sous un autre type de fichier (primaire) dans la **Solution Explorer**.

 Par exemple, le code suivant spécifie qu’un fichier codébehind IronPython est lié à un fichier .aspx. Lorsqu’une nouvelle page Web .aspx est créée dans une solution de site Web IronPython, un nouveau fichier source .py est généré et apparaît comme un nœud enfant de la page .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Cet attribut est placé sur l’ensemble du projet linguistique. Il sélectionne le fournisseur IntelliSense pour la langue.

 Par exemple, le code suivant précise qu’un exemple de PythonIntellisenseProvider, qui implémente, devrait être créé sur demande pour fournir des services linguistiques. <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 L’implémentation IVsIntellisenseProject gère les références et appelle le compilateur de langue lorsqu’une page Web avec code est demandée mais n’est pas mise en cache.

## <a name="see-also"></a>Voir aussi
- [Prise en charge de site web](../../extensibility/internals/web-site-support.md)
