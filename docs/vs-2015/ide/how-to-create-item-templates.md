---
title: Guide pratique pour créer des modèles d’élément | Microsoft Docs
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
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d16591f7650aec3eaebf08e1330b74dd425cc572
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496359"
---
# <a name="how-to-create-item-templates"></a>Guide pratique pour créer des modèles d’élément
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les étapes de la [première procédure](../ide/how-to-create-item-templates.md#export_template) de cette rubrique montrent comment créer un modèle d’élément à l’aide de l’Assistant **Exportation de modèle**. Si votre modèle se compose de plusieurs fichiers, consultez [Guide pratique pour créer des modèles d’élément multifichier](../ide/how-to-create-multi-file-item-templates.md).  
  
 L'Assistant exécute de nombreuses tâches à votre place pour créer le modèle de base mais, dans de nombreux cas, vous devez modifier manuellement le fichier .vstemplate après avoir exporté le modèle. Par exemple, si vous souhaitez que l’élément s’affiche dans la boîte de dialogue **Ajouter un nouvel élément** pour un projet d’application [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], vous devez effectuer quelques étapes supplémentaires. La [deuxième procédure](../ide/how-to-create-item-templates.md#modify_template) de cette rubrique vous aide à accomplir cette tâche.  
 
 Dans certains cas, il est possible que vous vouliez ou deviez créer un modèle d'élément manuellement à partir de zéro. La [troisième procédure](../ide/how-to-create-item-templates.md#create_template) montre comment procéder.  
  
 Consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md) pour plus d’informations sur les éléments qui peuvent être utilisés dans le fichier .vstemplate.  
  
### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Pour ajouter un modèle d'élément de projet personnalisé à la boîte de dialogue Ajouter un nouvel élément  
  
1.  Ouvrez ou créez un projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2.  Ajoutez un élément au projet et modifiez-le si vous le souhaitez.  
  
3.  Modifiez le fichier de code pour indiquer où le remplacement de paramètres doit avoir lieu. Pour plus d’informations, consultez [Guide pratique pour substituer des paramètres dans un modèle](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Dans le menu **Fichier**, cliquez sur **Exporter le modèle**.  
  
5.  Cliquez sur **Modèle d’élément**, sélectionnez le projet qui contient l’élément et cliquez sur **Suivant**.  
  
6.  Sélectionnez l’élément pour lequel vous souhaitez créer un modèle et cliquez sur **Suivant**.  
  
7.  Sélectionnez les références d’assembly à inclure dans le modèle et cliquez sur **Suivant**.  
  
8.  Tapez le nom du fichier icône, le nom de l’image d’aperçu, le nom du modèle et la description du modèle, puis cliquez sur **Terminer**.  
  
     Les fichiers du modèle sont ajoutés à un fichier .zip et copiés dans le répertoire que vous spécifiez dans la boîte de dialogue. L’emplacement par défaut est le dossier **..\Users\\<nom_utilisateur\>\Documents\Visual Studio \<version>\My Exported Templates\\**.  
  
    > [!WARNING]
    >  Dans les versions antérieures de Visual Studio, l’emplacement par défaut est **..\Users\\<nom_utilisateur\>\Documents\Visual Studio \<version>\Templates\ItemTemplates**.  
  
### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>Pour permettre l'utilisation du modèle d'élément dans un projet Windows Store  
  
1.  Appliquez les étapes de la procédure ci-dessus pour exporter un modèle d'élément.  
  
2.  Extrayez le fichier .vstemplate du fichier .zip qui a été copié dans le dossier \Users\\*nom_utilisateur*\Documents\Visual Studio *version*\Templates\ItemTemplates\ (ou **My Exported Templates**).  
  
3.  Ouvrez le fichier .vstemplate dans Visual Studio.  
  
4.  Pour un projet C# Windows Store pour Windows 8.1, dans le fichier .vstemplate, ajoutez le code XML suivant entre les balises d'ouverture et de fermeture `<TemplateData>` : `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`.  
  
     Un projet C++ Windows Store pour Windows 8.1 utilise la valeur `WinRT-Native-6.3`. Pour Windows 10 et d’autres types de projets, consultez [TemplateGroupID, élément (modèles Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md).  
  
     L'exemple suivant illustre le contenu complet d'un fichier .vstemplate après l'ajout de la ligne XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`. Cet exemple est spécifique aux projets C#. Vous pouvez modifier les éléments [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> <ProjectTpe> et \< pour spécifier d’autres types de projets et langages.  
  
    ```xml  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>MyItemStoreTemplate.xaml</DefaultName>  
        <Name>MyItemStoreTemplate</Name>  
        <Description>This is an example itemtemplate</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>10</SortOrder>  
        <Icon>__TemplateIcon.ico</Icon>  
        <TemplateGroupID>WinRT-Managed</TemplateGroupID>  
      </TemplateData>  
      <TemplateContent>  
        <References />  
        <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>  
        <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Pour connaître d’autres valeurs TemplateGroupID possibles, consultez [TemplateGroupID, élément (modèles Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md). Pour obtenir la référence complète de .vstemplate, consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
5.  Dans Visual Studio, enregistrez le fichier .vstemplate, puis fermez-le.  
  
6.  Copiez et collez le fichier .vstemplate dans le fichier .zip situé dans le dossier ..\Users\\*nom_utilisateur*\Documents\Visual Studio *version*\Templates\ItemTemplates\.  
  
     Si la boîte de dialogue **Copier le fichier** apparaît, sélectionnez l’option **Copier et remplacer**.  
  
 Vous pouvez maintenant ajouter un élément basé sur ce modèle à un projet [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] à l’aide de la boîte de dialogue **Ajouter un nouvel élément**.  
  
 Pour plus d’informations sur les noms de paramètres, consultez [Paramètres de modèle](../ide/template-parameters.md).  
  
### <a name="to-enable-templates-for-specific-project-sub-types"></a>Pour activer les modèles pour des sous-types de projet spécifiques  
  
1.  L'environnement de développement permet de mettre à disposition des éléments de projet à partir de la boîte de dialogue Ajouter un élément pour certains projets. Utilisez cette procédure pour que des éléments personnalisés soient disponibles pour des projets Windows, Web, Office ou de base de données.  
  
     Localisez l'élément ProjectType dans le fichier .vstemplate du modèle d'élément.  
  
     Ajoutez un élément [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) immédiatement après l’élément ProjectType.  
  
2.  Affectez au texte de l'élément l'une des valeurs suivantes :  
  
    1.  Windows  
  
    2.  Office  
  
    3.  Base de données  
  
    4.  Web  
  
     Par exemple : `<ProjectSubType>Database</ProjectSubType>`.  
  
     L'exemple suivant affiche un modèle d'élément disponible pour les projets Office.  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">  
        <TemplateData>  
            <Name>Class</Name>  
            <Description>An empty class file</Description>  
            <Icon>Class.ico</Icon>  
            <ProjectType>CSharp</ProjectType>  
            <ProjectSubType>Office</ProjectSubType>  
            <DefaultName>Class.cs</DefaultName>  
        </TemplateData>  
        <TemplateContent>  
            <ProjectItem>Class1.cs</ProjectItem>  
        </TemplateContent>  
    </VSTemplate>  
  
    ```  
  
### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Pour créer manuellement un modèle d'élément sans utiliser l'Assistant Exportation de modèle  
  
1.  Créez un projet et un élément de projet.  
  
2.  Modifiez l'élément de projet jusqu'à ce qu'il soit prêt à être enregistré en tant que modèle.  
  
3.  Selon le cas, modifiez le fichier de code pour indiquer où le remplacement de paramètres doit avoir lieu. Pour plus d'informations sur le remplacement de paramètres, consultez Comment : substituer des paramètres dans un modèle.  
  
4.  Créez un fichier XML et enregistrez-le à l'aide de l'extension de nom de fichier .vstemplate, dans le même répertoire que votre nouveau modèle d'élément.  
  
5.  Créez le fichier XML .vstemplate pour fournir des métadonnées de modèle d'élément. Pour plus d’informations, consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md) et l’exemple de la section précédente.  
  
6.  Enregistrez le fichier .vstemplate, puis fermez-le.  
  
7.  Dans l'Explorateur Windows, sélectionnez les fichiers à inclure dans votre modèle, cliquez avec le bouton droit sur la sélection, cliquez sur Envoyer vers, puis sur Dossier compressé. Les fichiers que vous avez sélectionnés sont compressés dans un fichier .zip.  
  
8.  Copiez le fichier .zip et collez-le à l'emplacement du modèle d'élément utilisateur. Dans Visual Studio 2015, le répertoire par défaut est... \Users\\< nom d’utilisateur\>\Documents\Visual Studio 2015\Templates\ItemTemplates\\. Pour plus d'informations, consultez Comment : localiser et organiser les modèles de projet et d'élément  
  
## <a name="see-also"></a>Voir aussi  
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Guide pratique pour créer des modèles d’élément multifichier](../ide/how-to-create-multi-file-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)