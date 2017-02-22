---
title: "Comment&#160;: cr&#233;er des mod&#232;les d&#39;&#233;l&#233;ment multifichier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles d'élément, créer des modèles d'élément multifichier"
  - "modèles d'élément multifichier"
  - "modèles Visual Studio, créer des modèles d'élément multifichier"
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Comment&#160;: cr&#233;er des mod&#232;les d&#39;&#233;l&#233;ment multifichier
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il arrive que les modèles d'élément spécifient un seul élément, mais quelquefois cet élément est composé de plusieurs fichiers.  Par exemple, un modèle d'élément Windows Forms pour Visual Basic requiert les trois fichiers suivants :  
  
-   Un fichier .vb qui contient le code du formulaire.  
  
-   Un fichier .designer.vb qui contient les informations relatives au concepteur.  
  
-   Un fichier .resx qui contient les ressources incorporées.  
  
 Les modèles d'éléments multifichier requièrent l'utilisation de paramètres garantissant que les extensions de nom de fichier appropriées sont utilisées lors de la création de l'élément dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si vous créez un modèle d'élément à l'aide de l'Assistant **Exportation de modèle**, ces paramètres sont générés automatiquement et aucune autre modification n'est requise.  Les étapes suivantes expliquent comment utiliser les paramètres pour garantir que les extensions de nom de fichier appropriées soient créées.  
  
### Pour créer manuellement un modèle d'élément à plusieurs fichiers  
  
1.  Créez le modèle d'élément de la même manière qu'un modèle d'élément à fichier unique.  Pour plus d'informations, consultez [Comment : créer des modèles d'élément](../ide/how-to-create-item-templates.md).  
  
2.  Ajoutez des attributs `TargetFileName` à chaque élément `ProjectItem`.  Donnez aux attributs `TargetFileName` les valeurs $fileinputname$.*ExtensionFichier*, où *ExtensionFichier* est l'extension du nom de fichier à inclure dans le modèle.  Par exemple :  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     Lorsque vous ajoutez à un projet un élément dérivé de ce modèle, les noms de fichiers sont basés sur le nom que l'utilisateur a entré dans la boîte de dialogue **Ajouter un nouvel élément**.  
  
3.  Sélectionnez les fichiers à inclure dans votre modèle, cliquez avec le bouton droit sur la sélection, cliquez sur **Envoyer vers** puis cliquez sur **Dossier compressé \(zippé\)**.  Les fichiers que vous avez sélectionnés sont compressés dans un fichier .zip.  
  
4.  Placez le fichier .zip à l'emplacement du modèle d'élément de l'utilisateur.  Par défaut, ce répertoire est \\My Documents\\Visual Studio *version*\\Templates\\ItemTemplates \\.  Pour plus d'informations, consultez [Comment : localiser et organiser les modèles](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## Exemple  
 L'exemple suivant affiche un modèle Windows Forms [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si vous créez un élément d'après ce modèle, les noms des trois fichiers créés correspondent aux noms entrés dans la boîte de dialogue **Ajouter un nouvel élément**.  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Voir aussi  
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Comment : créer des modèles d'élément](../ide/how-to-create-item-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Comment : substituer des paramètres dans un modèle](../ide/how-to-substitute-parameters-in-a-template.md)