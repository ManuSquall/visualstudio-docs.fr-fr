---
title: '&lt;personnalisations&gt; élément (développement Office dans Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ef7aa93494ef2b2a33ab4533e217bd37ccd07420
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;personnalisations&gt; élément (développement Office dans Visual Studio)
  L’élément `customizations` de l’espace de noms `vstov4` contient toutes les informations sur l’installation et le chargement de chaque solution Office.  
  
## <a name="syntax-for-document-level-customizations"></a>Syntaxe pour les personnalisations au niveau du document  
  
```xml
<customizations>  
  <customization  
    id  
    <document  
      solutionId  
    />  
  </customization>  
</customizations>  
```  
  
## <a name="syntax-for-vsto-add-ins"></a>Syntaxe pour les compléments VSTO  
  
```xml
<customizations>  
  <customization  
    id  
    <appAddin  
      application  
      loadBehavior  
      keyName>  
    <friendlyName></friendlyName>  
    <description></description>  
    <formRegions></formRegions>  
  </customization>  
</customizations>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `customizations` contient des informations spécifiques sur chaque solution Office. Cet élément doit figurer dans l’espace de noms suivant : `vstov4=urn:schemas-microsoft-com:vsto.v4`. Les éléments enfants de l’assembly doivent également figurer dans cet espace de noms.  
  
 L’élément `customizations` ne possède pas d’attributs.  
  
 L’élément `customizations` possède l’élément enfant suivant.  
  
### <a name="customization"></a>Personnalisation  
 Obligatoire. Le `customization` élément dans le `vstov4` espace de noms est défini dans [ &#60;personnalisation&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## <a name="example-of-a-document-level-customization"></a>Exemple d’une personnalisation au niveau du document  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre l’élément `customizations` d’une personnalisation au niveau du document.  
  
> [!NOTE]  
>  Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml
<vstov4:customizations   
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
  <vstov4:customization>  
    <vstov4:document   
      solutionId="73e" />  
  </vstov4:customization>  
</vstov4:customizations>  
```  
  
## <a name="example-of-an-vsto-add-in"></a>Exemple de complément VSTO  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre l’élément `customizations` d’un complément VSTO. Il s’agit d’un complément VSTO Outlook qui inclut des zones de formulaire. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml
<vstov4:customizations   
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
  <vstov4:customization>  
    <vstov4:appAddIn   
      application="Outlook"   
      loadBehavior="3"   
      keyName="ContosoOutlookAddIn">  
      <vstov4:friendlyName>  
        ContosoOutlookAddIn  
      </vstov4:friendlyName>  
      <vstov4:description>  
        ContosoOutlookAddIn - Outlook VSTO Add-in   
        created with Visual Studio Tools for Office  
      </vstov4:description>  
      <vstov4:formRegions>  
        <vstov4:formRegion  
            name="OutlookAddIn1.FormRegion1">  
          <vstov4:messageClass name="IPM.Note" />  
          <vstov4:messageClass name="IPM.Contact" />  
          <vstov4:messageClass name="IPM.Appointment" />  
        </vstov4:formRegion>  
      </vstov4:formRegions>  
    </vstov4:appAddIn>  
  </vstov4:customization>  
</vstov4:customizations>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  