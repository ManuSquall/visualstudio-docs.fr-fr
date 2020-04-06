---
title: CATIDs pour les objets qui sont généralement utilisés pour étendre les projets (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5754e53f24731eb44dba128ccfcf4b474e833d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709866"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>CATIDs pour les objets qui sont généralement utilisés pour étendre les projets
Le tableau suivant répertorie les `Project` CATID qui sont utilisés pour étendre `ProjectItem` et automatiser les objets pour [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], et [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] les projets. Ces CATIDs sont définis dans *VSLangProj.olb*.

## <a name="listing-of-catids"></a>Liste des CATID

|Nom|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|610D4614-D0D5-11D2-8599-006097C68E81|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|610D4615-D0D5-11D2-8599-006097C68E81|

## <a name="visual-basic-catids"></a>CATIDs de base visuelle
 Le tableau suivant répertorie les [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] CATID qui sont utilisés pour étendre les objets de navigation. Ils sont tous définis dans *VSLangProj.olb*.

|Nom|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|E0FDC879-C32A-4751-A3D3-0B3824BD575F|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|67F8DD11-14EB-489b-87F0-F01C52AF3870|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|EA5BD05D-3C72-40A5-95A0-28A2773311CA|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|932DC619-2EAA-4192-B7E6-3D15AD31DF49|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|2289B812-8191-4e81-B7B3-174045AB0CB5|

## <a name="visual-c-catids"></a>Visuels C C-CATIDs
 Les CATID suivants peuvent être [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] utilisés pour étendre les objets de navigation. Ils sont tous définis dans *VSLangProj.olb*.

|Nom|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|4EF9F003-DE95-4d60-96B0-212979F2A857|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|A12CE10A-227F-4963-ADB6-3A43388513CA|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|8D58E6AF-ED4E-48B0-8C7B-C74EF0735451|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|914FE278-054A-45DB-BF9E-5F22484CC84C|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27|

## <a name="c-catids"></a>CATIDs CMD
 Le [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] système de projet suivant CATIDs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne sont pas exposés dans les bibliothèques de type dans .NET 2003 et doivent être inclus dans votre code chaque fois que vous voulez étendre ces objets de projet. Ces CATID seront inclus dans les bibliothèques [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de type dans les versions ultérieures de .

|Nom|GUID|
|----------|----------|
|`CVCProjectNode`|EE8299CB-19B6-4f20-ABEA-E1FD9A33B683|
|`CVCFolderNode`|EE8299CA-19B6-4f20-ABEA-E1FD9A33B683|
|`CVCFileNode`|EE8299C9-19B6-4f20-ABEA-E1FD9A33B683|

 L’exemple de code suivant montre comment programmer ces CATID dans votre code.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Le [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] système de projet suivant CATIDs ne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sont pas non plus exposés dans les bibliothèques de type dans .NET 2003 et doivent être inclus dans votre code chaque fois que vous voulez étendre ces objets de projet. Ces CATIDs ne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sont disponibles que dans .NET 2003 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]et ne seront pas disponibles dans les versions ultérieures de .

|Nom|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|FE8299C9-19B6-4f20-ABEA-E1FD9A33B683|
|`CVCProjectReferenceNode`|593DCFCE-20A7-48e4-ACA1-49ADE9049887|
|`CVCActiveXReferenceNode`|9E8182D3-C60A-44f4-A74B-14C90EF9CACE|
|`CVCReferences`|FE8299CA-19B6-4f20-ABEA-E1FD9A33B683|

 L’exemple de code suivant montre comment programmer ces CATID dans votre code :

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Les GUIDs [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] pour [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] les types et les types de projet sont indiqués dans le tableau suivant.

| Type de projet | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | FAE04EC0-301F-11D3-BF4B-00C04F79EFBC |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | F184B08F-C81C-45F6-A57F-5ABD9991F28F |

## <a name="see-also"></a>Voir aussi
- [Ajouter des modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Enregistrer les modèles de projets et d’objets](../../extensibility/internals/registering-project-and-item-templates.md)
