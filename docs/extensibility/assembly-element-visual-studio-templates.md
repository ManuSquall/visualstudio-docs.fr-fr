---
title: "Assembly, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Assembly"
helpviewer_keywords: 
  - "Assembly, élément [modèles Visual Studio]"
  - "<Assembly>, élément [modèles Visual Studio]"
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Assembly, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Donne des informations sur un assembly dont le modèle ajoute une référence dans les projets.  
  
## Syntaxe  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Référence](../extensibility/reference-element-visual-studio-templates.md)|Spécifie la référence d'assembly à ajouter lorsque l'élément est ajouté à un projet.|  
  
## Valeur texte  
 Une valeur texte est requise.  
  
 Ce texte spécifie l'assembly à ajouter à un projet lorsque le modèle d'élément est instancié.  Le nom de l'assembly doit être spécifié d'une des manières suivantes :  
  
-   En tant que nom complet de l'assembly.  Par exemple :  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Comme simple référence de texte.  Par exemple :  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## Notes  
 L'élément `Assembly` est un enfant obligatoire de l'élément `Reference`.  
  
 Les éléments `Reference`, `References,` et `Assembly` ne peuvent être utilisés que dans les fichiers .vstemplate dont l'attribut `Type` a la valeur `Item`.  
  
## Exemple  
 L'exemple suivant illustre l'élément `TemplateContent` d'un modèle d'élément.  Ce XML ajoute des références aux assemblys System.dll et System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)