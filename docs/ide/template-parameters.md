---
title: "Paramètres de modèle | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
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
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7218b5bdcc95ed5db7f87c6fb17230895db579cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="template-parameters"></a>Paramètres de modèle
L’utilisation de paramètres dans vos modèles vous permet de remplacer les valeurs des parties principales du modèle, telles que les noms de classes et les espaces de noms, quand le modèle est instancié. Ces paramètres sont remplacés par l’Assistant Modèle qui s’exécute en arrière-plan quand un utilisateur clique sur **OK** dans les boîtes de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.  
  
## <a name="declaring-and-enabling-template-parameters"></a>Déclaration et activation des paramètres de modèle  
 Les paramètres de modèle sont déclarés au format $*paramètre*$. Exemple :  
  
-   $safeprojectname$  
  
-   $guid1$  
  
-   $guid5$  
  
#### <a name="to-enable-parameter-substitution-in-templates"></a>Pour activer la substitution des paramètres dans les modèles  
  
1.  Dans le fichier .vstemplate du modèle, localisez l’élément `ProjectItem` qui correspond à l’élément pour lequel vous souhaitez activer le remplacement des paramètres.  
  
2.  Affectez à l'attribut `ReplaceParameters` de l'élément `ProjectItem` la valeur `true`.  
  
3.  Dans le fichier de code de l’élément de projet, ajoutez les paramètres quand cela est approprié. Par exemple, le paramètre suivant spécifie que le nom du projet sécurisé doit être utilisé pour désigner l’espace de noms dans un fichier :  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## <a name="reserved-template-parameters"></a>Paramètres de modèle réservés  
 Le tableau suivant liste les paramètres de modèle réservés qui peuvent être utilisés par n’importe quel modèle.  
  
> [!NOTE]
>  Les paramètres de modèle respectent la casse.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`clrversion`|Version actuelle du Common Language Runtime (CLR).|  
|`GUID [1-10]`|GUID utilisé pour remplacer le GUID du projet dans un fichier projet. Vous pouvez spécifier jusqu’à 10 GUID uniques (par exemple, `guid1)`.|  
|`itemname`|Nom fourni par l’utilisateur dans la boîte de dialogue **Ajouter un nouvel élément**.|  
|`machinename`|Nom de l’ordinateur actuel (par exemple, Ordi01).|  
|`projectname`|Nom fourni par l’utilisateur dans la boîte de dialogue **Nouveau projet**.|  
|`registeredorganization`|Valeur de clé de Registre provenant de HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|  
|`rootnamespace`|Espace de noms racine du projet actuel. Ce paramètre s’applique uniquement aux modèles d’élément.|  
|`safeitemname`|Nom fourni par l’utilisateur dans la boîte de dialogue **Ajouter un nouvel élément**, dont tous les caractères et espaces potentiellement dangereux ont été supprimés.|  
|`safeprojectname`|Nom fourni par l’utilisateur dans la boîte de dialogue **Nouveau projet**, dont tous les caractères et espaces potentiellement dangereux ont été supprimés.|  
|`time`|Date et heure actuelles au format JJ/MM/AAAA 00:00:00.|  
|`SpecificSolutionName`|Nom du fichier solution. Quand l’option "créer le répertoire de la solution" est cochée, `SpecificSolutionName` porte le nom de la solution. Quand l’option "créer le répertoire de solution" n’est pas cochée, `SpecificSolutionName` est vide.|  
|`userdomain`|Domaine de l’utilisateur actuel.|  
|`username`|Nom de l’utilisateur actuel.|  
|`webnamespace`|Nom du site web actuel. Ce paramètre est utilisé dans le modèle de formulaire web pour garantir des noms de classes uniques. Si le site web se trouve est dans le répertoire racine du serveur web, ce paramètre de modèle correspond au répertoire racine du serveur web.|  
|`year`|Année actuelle au format AAAA.|  
  
## <a name="custom-template-parameters"></a>Paramètres de modèle personnalisés  
 Vous pouvez spécifier vos propres paramètres et valeurs de modèle, en plus des paramètres de modèle réservés par défaut utilisés lors du remplacement de paramètres. Pour plus d’informations, consultez [CustomParameters, élément (modèles Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).  
  
## <a name="example-replacing-files-names"></a>Exemple : Remplacement de noms de fichiers  
 Vous pouvez spécifier des noms de fichiers de variables pour les éléments de projet à l’aide d’un paramètre ayant l’attribut `TargetFileName`. Par exemple, vous pouvez spécifier que le fichier .exe utilise comme nom le nom du projet, spécifié par `$projectname$`.  
  
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
  
## <a name="example-using-the-project-name-for-the-namespace-name"></a>Exemple : Utilisation du nom du projet comme nom de l’espace de noms  
 Pour utiliser le nom du projet pour l’espace de noms dans un fichier de classe Visual C#, Class1.cs, utilisez la syntaxe suivante :  
  
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
  
 Dans le fichier .vstemplate du modèle de projet, ajoutez le code XML suivant quand vous référencez le fichier Class1.cs :  
  
```  
<TemplateContent>  
    <ProjectItem ReplaceParameters="true">  
        Class1.cs  
    </ProjectItem>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)