---
title: Guide pratique pour créer manuellement des modèles web | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d84a71d54f178574e7aba719f4189b35312ec03
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505049"
---
# <a name="how-to-manually-create-web-templates"></a>Comment : créer manuellement des modèles Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : créer manuellement des modèles Web](https://docs.microsoft.com/visualstudio/ide/how-to-manually-create-web-templates).  
  
La création d’un modèle web est différente de la création d’autres types de modèles. Étant donné que les modèles de projet web apparaissent dans la boîte de dialogue **Ajouter un nouveau site web** et que les éléments de projet web sont classés par langage de programmation, le fichier .vstemplate doit spécifier le modèle comme modèle web et identifier le langage de programmation.  
  
> [!NOTE]
>  Les modèles web doivent contenir un fichier .webproj vide, spécifié avec l’attribut `File` de l’élément `Project`. Bien que les projets web ne nécessitent pas de fichiers projet, ce fichier est indispensable au bon fonctionnement du modèle web.  
  
### <a name="to-manually-create-a-web-template"></a>Pour créer manuellement un modèle web  
  
1.  Créez un projet web.  
  
2.  Modifiez ou supprimez les fichiers du projet, ou ajoutez de nouveaux fichiers au projet.  
  
3.  Créez un fichier XML et enregistrez-le à l’aide de l’extension de nom de fichier .vstemplate dans le même répertoire que votre projet. Ne l’ajoutez pas au projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Créez le fichier XML .vstemplate pour fournir les métadonnées du modèle de projet. Pour plus d’informations, consultez l’exemple de la section suivante.  
  
5.  Localisez l’élément `ProjectType` dans le fichier .vstemplate, puis affectez au texte la valeur `Web`.  
  
6.  Après l’élément `ProjectType`, ajoutez un élément `ProjectSubType` et affectez au texte la valeur du langage de programmation du modèle. Voici les valeurs pouvant être affectées comme langage de programmation :  
  
    -   CSharp  
  
    -   VisualBasic  
  
     Exemple :  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  Sélectionnez les fichiers présents dans votre modèle (cela inclut le fichier .vstemplate), cliquez avec le bouton droit sur la sélection, cliquez sur **Envoyer vers**, puis cliquez sur **Dossier compressé**. Les fichiers sont compressés dans un fichier .zip.  
  
8.  Placez le fichier de modèle .zip dans le répertoire du modèle de projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Par défaut, ce répertoire est \Mes documents\Visual Studio *Version*\My Exported Templates\\.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affiche un fichier .vstemplate de base pour un modèle de projet web.  
  
```  
<VSTemplate Version="2.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)



