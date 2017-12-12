---
title: "Guide pratique pour créer des modèles d’élément multifichier | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e3e1f6c6e62494f040e2f52180c5588688f460db
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-multi-file-item-templates"></a>Guide pratique pour créer des modèles d'élément multifichier
Il arrive que les modèles d’élément spécifient un seul élément, mais cet élément est parfois composé de plusieurs fichiers. Par exemple, un modèle d’élément Windows Forms pour Visual Basic nécessite les trois fichiers suivants :  
  
-   Un fichier .vb qui contient le code du formulaire.  
  
-   Un fichier .designer.vb qui contient les informations relatives au concepteur du formulaire.  
  
-   Un fichier .resx qui contient les ressources incorporées du formulaire.  
  
 Les modèles d’élément multifichier exigent des paramètres pour garantir que les extensions de nom de fichier appropriées sont utilisées lors de la création de l’élément dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si vous créez un modèle d’élément à l’aide de l’Assistant **Exportation de modèle**, ces paramètres sont générés automatiquement et aucune autre modification n’est nécessaire. Les étapes suivantes expliquent comment utiliser les paramètres pour garantir que les extensions de nom de fichier appropriées soient créées.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Pour créer manuellement un modèle d’élément multifichier  
  
1.  Créez le modèle d’élément de la même manière qu’un modèle d’élément à fichier unique. Pour plus d’informations, consultez [Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md).  
  
2.  Ajoutez des attributs `TargetFileName` à chaque élément `ProjectItem`. Affectez aux attributs `TargetFileName` la valeur $fileinputname$.*FileExtension*, où *FileExtension* est l’extension du nom du fichier qui est inclut dans le modèle. Exemple :  
  
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
  
     Quand vous ajoutez à un projet un élément dérivé de ce modèle, les noms de fichiers sont basés sur le nom que l’utilisateur a entré dans la boîte de dialogue **Ajouter un nouvel élément**.  
  
3.  Sélectionnez les fichiers à inclure dans votre modèle, cliquez avec le bouton droit sur la sélection, cliquez sur **Envoyer vers**, puis cliquez sur **Dossier compressé**. Les fichiers que vous avez sélectionnés sont compressés dans un fichier .zip.  
  
4.  Placez le fichier .zip à l’emplacement du modèle d’élément utilisateur. Par défaut, ce répertoire est \Mes documents\Visual Studio *Version*\Templates\ItemTemplates\\. Pour plus d’informations, consultez [Guide pratique pour localiser et organiser les modèles](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant présente un modèle Windows Forms [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Quand vous créez un élément à partir de ce modèle, les noms des trois fichiers créés correspondent aux noms entrés dans la boîte de dialogue **Ajouter un nouvel élément**.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Guide pratique pour substituer des paramètres dans un modèle](../ide/how-to-substitute-parameters-in-a-template.md)