---
title: "CATID des objets qui sont g&#233;n&#233;ralement utilis&#233;s pour &#233;tendre des projets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, CATID"
  - "GUID, les packages VS"
  - "CATID de packages VS"
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# CATID des objets qui sont g&#233;n&#233;ralement utilis&#233;s pour &#233;tendre des projets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le tableau suivant répertorie CATIDs utilisés pour étendre `Project` et des objets Automation `ProjectItem` pour [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], et les projets de[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] .  ces CATIDs sont définis dans VSLangProj.olb.  
  
## Liste de CATIDs  
  
|Nom|GUID|  
|---------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614\-D0D5\-11D2\-8599\-006097 C68 E81}|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615\-D0D5\-11D2\-8599\-006097 C68 E81}|  
  
## Visual Basic CATIDs  
 Le tableau suivant répertorie CATIDs utilisés pour étendre [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] parcourez des objets.  Ils sont tous définis dans VSLangProj.olb.  
  
|Nom|GUID|  
|---------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FD C879 \- C32 A\-4751\-A3D3\-0B3824BD575F}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11\-14EB\-489b\-87F0\-F01 C52 AF3870}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D\-3 C72 \-40A5\-95A0\-28A2773311CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932D C619 \-2EAA\-4192\-B7E6\-3D15AD31DF49}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812\-8191\-4e81\-B7B3\-174045AB0 CB5}|  
  
## Visual c\# CATIDs  
 Le CATIDs suivant peut être utilisé pour étendre [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] parcourez des objets.  Ils sont tous définis dans VSLangProj.olb.  
  
|Nom|GUID|  
|---------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{} 4EF9F003\-DE95\-4d60\-96B0\-212979F2A857|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12 CE10 A\-227F\-4963\-ADB6\-3A43388513CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF\-ED4E\-48B0\-8 C7 b C74 EF0735451}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278\-054A\-45DB\-BF9E\-5F22484 CC84 C}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8\- C855 \-4a4e\-95A5\- CB45 C67 D6 C27}|  
  
## C\+\+ CATIDs  
 Le système de projet suivant CATIDs de [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] ne sont pas exposés aux bibliothèques de types dans le.NET framework 2003 sur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et doivent être inclus dans votre code chaque fois que vous souhaitez étendre ces objets de projet.  Ces CATIDs sera inclus dans les bibliothèques de types dans les versions ultérieures de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Nom|GUID|  
|---------|----------|  
|`CVCProjectNode`|{} EE8299CB\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
|`CVCFolderNode`|{} EE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
|`CVCFileNode`|{EE8299 C9 \-19B6\-4F20\-ABEA\-E1FD9A33B683}|  
  
 L'exemple de code suivant montre comment programmer ces CATIDs dans votre code.  
  
```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Le système de projet suivant CATIDs de [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] ne sont pas exposés aux bibliothèques de types dans le.NET framework 2003 sur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et doivent être inclus dans votre code chaque fois que vous souhaitez étendre ces objets de projet.  Ces CATIDs sont uniquement disponible dans.NET 2003 de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]et ne seront pas disponibles dans les versions ultérieures de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Nom|GUID|  
|---------|----------|  
|`CVCAssemblyReferenceNode` **:**|{FE8299 C9 \-19B6\-4F20\-ABEA\-E1FD9A33B683}|  
|`CVCProjectReferenceNode`|{593DCFCE\-20A7\-48e4\-A CA1 \-49ADE9049887}|  
|`CVCActiveXReferenceNode`|{9E8182D3\- C60 A\-44f4\-A74B\-14 C90 EF9CACE}|  
|`CVCReferences`|{} FE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
  
 L'exemple de code suivant montre comment programmer ces CATIDs dans votre code :  
  
```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Les GUID pour les types de projet de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sont présentés dans le tableau suivant.  
  
|Type de projet|GUID|  
|--------------------|----------|  
|[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]|{FAE04E C0 \-301F\-11D3\-BF4B\-00 C04 F79EFBC}|  
|[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]|{F184B08F\- C81 C\-45F6\-A57F\-5ABD9991F28F}|  
  
## Voir aussi  
 [Ajout de projet et modèles d'élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md)