---
title: "Comment&#160;: cr&#233;er manuellement des mod&#232;les Web | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles de projet (Visual Studio), Web"
  - "modèles (Visual Studio), Web"
  - "modèles Visual Studio, Web"
  - "modèles Web (Visual Studio)"
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment&#160;: cr&#233;er manuellement des mod&#232;les Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La création d'un modèle Web est différente de la création des autres types de modèles.  Comme les modèles de projet Web apparaissent dans la boîte de dialogue **Ajouter un nouveau site Web** et que les éléments de projet Web sont catégorisés par langage de programmation, le fichier .vstemplate doit spécifier le modèle en tant que modèle Web et identifier le langage de programmation.  
  
> [!NOTE]
>  Les modèles Web doivent contenir un fichier .webproj vide, spécifié avec l'attribut `File` de l'élément `Project`.  Bien que les projets Web ne requièrent pas de fichiers projet, ce fichier est indispensable au bon fonctionnement du modèle Web.  
  
### Pour créer un modèle Web manuellement  
  
1.  Créez un projet Web.  
  
2.  Modifiez ou supprimez les fichiers du projet ou ajoutez de nouveaux fichiers au projet.  
  
3.  Créez un fichier XML et enregistrez\-le dans le même répertoire que votre projet, en utilisant une extension de nom de fichier .vstemplate.  Ne l'ajoutez pas au projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Créez le fichier XML .vstemplate pour fournir les métadonnées du modèle de projet.  Pour plus d'informations, consultez l'exemple de la section suivante.  
  
5.  Localisez l'élément `ProjectType` dans le fichier .vstemplate et donnez au texte la valeur `Web`.  
  
6.  Après l'élément `ProjectType`, ajoutez un élément `ProjectSubType` et donnez au texte la valeur du langage de programmation du modèle.  Voici les valeurs pouvant être données comme langage de programmation :  
  
    -   CSharp  
  
    -   VisualBasic  
  
     Par exemple :  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  Sélectionnez les fichiers inclus dans votre modèle \(y compris le fichier .vstemplate\), cliquez avec le bouton droit sur la sélection, cliquez sur **Envoyer vers** puis sur **Dossier compressé \(zippé\)**.  Les fichiers sont compressés dans un fichier .zip.  
  
8.  Placez le fichier modèle .zip dans le répertoire du modèle de projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  par défaut, ce répertoire est \\My Documents\\Visual Studio *version*\\My Exported Templates \\.  
  
## Exemple  
 L'exemple suivant affiche un fichier .vstemplate de base pour un modèle de projet Web.  
  
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
  
## Voir aussi  
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)