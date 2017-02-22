---
title: "Param&#232;tres de mod&#232;le | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles d'élément, paramètres"
  - "modèles de projet, paramètres"
  - "paramètres de modèle (Visual Studio)"
  - "modèles Visual Studio, paramètres"
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Param&#232;tres de mod&#232;le
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En utilisant des paramètres dans vos modèles, remplacez les valeurs des principales parties du modèle telles que les noms de classes et espaces de noms, lorsque le modèle est instancié.  Ces paramètres sont remplacés par l'Assistant de modèle qui s'exécute en arrière\-plan lorsqu'un utilisateur clique sur **OK** dans les boîtes de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.  
  
## Déclaration et activation des paramètres d'un modèle  
 Les paramètres d'un modèle sont déclarés dans le format $*parameter*$.  Par exemple :  
  
-   $nomprojetfiable$  
  
-   $guid1$  
  
-   $guid5$  
  
#### Pour activer la substitution de paramètres dans les modèles  
  
1.  Dans le fichier .vstemplate du modèle, localisez l'élément `ProjectItem` qui correspond à l'élément pour lequel vous souhaitez activer le remplacement de paramètre.  
  
2.  Donnez à l'attribut `ReplaceParameters` de l'élément `ProjectItem` la valeur `true`.  
  
3.  Dans le fichier de code de l'élément de projet, incluez les paramètres aux emplacements appropriés.  Par exemple, le paramètre suivant spécifie que nomprojetfiable sera utilisé pour désigner l'espace de noms dans un fichier :  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## Paramètres de modèle réservés  
 Le tableau suivant répertorie les paramètres de modèle réservés qui peuvent être utilisés dans tout modèle.  
  
> [!NOTE]
>  Les paramètres de modèle respectent la casse.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`clrversion`|Version actuelle du Common Language Runtime \(CLR\).|  
|`GUID [1-10]`|GUID utilisé pour remplacer le GUID du projet dans un fichier projet.  Vous pouvez spécifier jusqu'à 10 GUID uniques \(par exemple, `guid1)`.|  
|`itemname`|Nom fourni par l'utilisateur dans la boîte de dialogue **Ajouter un nouvel élément**.|  
|`machinename`|Nom de l'ordinateur actuel \(par exemple, Ordi01\).|  
|`projectname`|Nom fourni par l'utilisateur dans la boîte de dialogue **Nouveau projet**.|  
|`registeredorganization`|Valeur de la clé de Registre tirée de HKLM\\Software\\Microsoft\\Windows NT\\CurrentVersion\\RegisteredOrganization.|  
|`rootnamespace`|Espace de noms racine du projet actuel.  Ce paramètre s'applique uniquement aux modèles d'élément.|  
|`safeitemname`|Nom fourni par l'utilisateur dans la boîte de dialogue **Ajouter un nouvel élément**, dont tous les caractères et espaces potentiellement dangereux ont été supprimés.|  
|`safeprojectname`|Nom fourni par l'utilisateur dans la boîte de dialogue **Nouveau projet**, dont tous les caractères et espaces potentiellement dangereux ont été supprimés.|  
|`time`|Date et heure actuelles au format JJ\/MM\/AAAA 00:00:00.|  
|`SpecificSolutionName`|Nom de la solution.  Lorsque « créer le répertoire de la solution » est activée, `SpecificSolutionName` contient le nom de la solution.  Lorsque « créer le répertoire de la solution » n'est pas activé, `SpecificSolutionName` est vide.|  
|`userdomain`|Domaine d'utilisateur actuel.|  
|`username`|Nom de l'utilisateur actuel.|  
|`webnamespace`|Nom du site Web en cours.  Ce paramètre est utilisé dans le modèle de formulaire Web pour garantir des noms de classe uniques.  Si le site Web se situe dans le répertoire racine du serveur Web, ce paramètre de modèle se résout en répertoire racine du serveur Web.|  
|`year`|Année actuelle au format AAAA.|  
  
## Paramètres des modèles personnalisés  
 Spécifiez vos propres paramètres et valeurs de modèle en plus des paramètres de modèle réservés utilisés lors du remplacement de paramètres. Pour plus d'informations, consultez [CustomParameters, élément \(modèles Visual Studio\)](../extensibility/customparameters-element-visual-studio-templates.md)  
  
## Exemple : Remplacement de noms de fichiers  
 Vous pouvez spécifier des noms de fichiers de variables pour les éléments de projet à l'aide d'un paramètre avec l'attribut `TargetFileName`.  Par exemple, vous pourriez spécifier que le fichier .exe prendra comme nom le nom du projet, spécifié par `$projectname$`.  
  
```  
<TemplateContent>  
    <ProjectItem  
        ReplaceParameters="true"  
        TargetFileName="$projectname$.exe">  
            File1.exe  
    </ProjectItem>  
      ...  
</TemplateContent>  
```  
  
## Exemple : Utilisation du nom du projet comme nom de l'espace de noms  
 Pour que le projet et l'espace de noms portent le même nom dans le fichier de classe Visual C\# Class1.cs, utilisez la syntaxe suivante :  
  
```  
#region Using directives  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
#endregion  
  
namespace $safeprojectname$  
{  
    public class Class1  
        {  
            public Class1()  
                {  
  
                }  
         }  
}  
```  
  
 Dans le fichier .vstemplate du modèle de projet, incluez le XML suivant lorsque vous référencez le fichier Class1.cs :  
  
```  
<TemplateContent>  
    <ProjectItem ReplaceParameters="true">  
        Class1.cs  
    </ProjectItem>  
    ...  
</TemplateContent>  
```  
  
## Voir aussi  
 [Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)