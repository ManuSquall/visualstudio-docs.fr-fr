---
title: "Paramètres de projet et de modèle d’élément Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e3ce315cd1ddff9445c72f7299a8d6aaf0a3a82
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="template-parameters"></a>Paramètres de modèle

L’utilisation de paramètres dans vos modèles vous permet de remplacer les valeurs des parties principales du modèle, telles que les noms de classes et les espaces de noms, quand le modèle est instancié. Ces paramètres sont remplacés par l’Assistant Modèle qui s’exécute en arrière-plan quand un utilisateur choisit **OK** ou **Ajouter** dans les boîtes de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.

## <a name="declaring-and-enabling-template-parameters"></a>Déclaration et activation des paramètres de modèle

Les paramètres de modèle sont déclarés au format $*paramètre*$. Exemple :

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="to-enable-parameter-substitution-in-templates"></a>Pour activer la substitution des paramètres dans les modèles

1. Dans le fichier .vstemplate du modèle, localisez l’élément `ProjectItem` qui correspond à l’élément pour lequel vous souhaitez activer le remplacement des paramètres.

1. Affectez à l'attribut `ReplaceParameters` de l'élément `ProjectItem` la valeur `true`.

1. Dans le fichier de code de l’élément de projet, ajoutez les paramètres quand cela est approprié. Par exemple, le paramètre suivant spécifie que le nom du projet sécurisé doit être utilisé pour désigner l’espace de noms dans un fichier :

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Paramètres de modèle réservés

Le tableau suivant liste les paramètres de modèle réservés qui peuvent être utilisés par n’importe quel modèle.

|Paramètre|Description|
|---------------|-----------------|
|clrversion|Version actuelle du Common Language Runtime (CLR).|
|guid[1-10]|GUID utilisé pour remplacer le GUID du projet dans un fichier projet. Vous pouvez spécifier jusqu’à 10 GUID uniques (par exemple, `guid1`).|
|itemname|Nom fourni par l’utilisateur dans la boîte de dialogue **Ajouter un nouvel élément**.|
|machinename|Nom de l’ordinateur actuel (par exemple, Ordi01).|
|projectname|Nom fourni par l’utilisateur dans la boîte de dialogue **Nouveau projet**.|
|registeredorganization|Valeur de clé de Registre provenant de HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|rootnamespace|Espace de noms racine du projet actuel. Ce paramètre s’applique uniquement aux modèles d’élément.|
|safeitemname|Nom fourni par l’utilisateur dans la boîte de dialogue **Ajouter un nouvel élément**, dont tous les caractères et espaces potentiellement dangereux ont été supprimés.|
|safeprojectname|Nom fourni par l’utilisateur dans la boîte de dialogue **Nouveau projet**, dont tous les caractères et espaces potentiellement dangereux ont été supprimés.|
|heure|Date et heure actuelles au format JJ/MM/AAAA 00:00:00.|
|SpecificSolutionName|Nom du fichier solution. Quand l’option "créer le répertoire de la solution" est cochée, `SpecificSolutionName` porte le nom de la solution. Quand l’option "créer le répertoire de solution" n’est pas cochée, `SpecificSolutionName` est vide.|
|userdomain|Domaine de l’utilisateur actuel.|
|Nom d’utilisateur|Nom de l’utilisateur actuel.|
|webnamespace|Nom du site web actuel. Ce paramètre est utilisé dans le modèle de formulaire web pour garantir des noms de classes uniques. Si le site web se trouve est dans le répertoire racine du serveur web, ce paramètre de modèle correspond au répertoire racine du serveur web.|
|année|Année actuelle au format AAAA.|

> [!NOTE]
> Les paramètres de modèle respectent la casse.

## <a name="custom-template-parameters"></a>Paramètres de modèle personnalisés

Vous pouvez spécifier vos propres paramètres et valeurs de modèle, en plus des paramètres de modèle réservés par défaut utilisés lors du remplacement de paramètres. Pour plus d’informations, consultez [CustomParameters, élément (modèles Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-using-the-project-name-for-a-file-name"></a>Exemple : Utilisation du nom du projet comme nom de fichier

Vous pouvez spécifier des noms de fichiers de variables pour les éléments de projet à l’aide d’un paramètre dans l’attribut `TargetFileName`.

L’exemple suivant spécifie que le nom d’un fichier exécutable utilise le nom du projet, spécifié par `$projectname$`.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-using-the-safe-project-name-for-the-namespace-name"></a>Exemple : Utilisation du nom du projet sécurisé comme nom de l’espace de noms

Pour utiliser le nom du projet sécurisé pour l’espace de noms dans un fichier de classe C#, utilisez la syntaxe suivante :

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

Dans le fichier .vstemplate du modèle de projet, ajoutez l’attribut `ReplaceParameters="true"` quand vous référencez le fichier :

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Voir aussi

[Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)  
[Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md)