---
title: "Sp&#233;cifiant l’emplacement du fichier de package VS &#224; l’interpr&#233;teur de commandes de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages gérés, emplacement du fichier"
  - "Les VSPackages, gérés d’emplacement de fichier de package"
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Sp&#233;cifiant l’emplacement du fichier de package VS &#224; l’interpr&#233;teur de commandes de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit être en mesure de localiser l’assembly DLL à charger le VSPackage. Vous pouvez le localiser de différentes manières, comme décrit dans le tableau suivant.  
  
|Méthode|Description|  
|-------------|-----------------|  
|Utilisez la clé de Registre CodeBase.|La clé de la base de code peut être utilisée pour diriger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour charger l’assembly VSPackage à partir de n’importe quel chemin d’accès de fichier complet. La valeur de la clé doit être le chemin d’accès à la DLL. Ceci est la meilleure façon d’avoir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de charger l’assembly de votre package. Cette technique est parfois appelée « CodeBase\/privée installation directory technique. » Lors de l’enregistrement la valeur de la base de code est passée pour les classes d’attributs de l’inscription via une instance de la <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> type.|  
|Placez le DLL dans le **PrivateAssemblies** active.|Placez l’assembly dans le **PrivateAssemblies** sous\-répertoire de le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] active. Assemblys situés dans **PrivateAssemblies** sont détectées automatiquement, mais ne sont pas visibles dans le **Ajouter des références** boîte de dialogue. La différence entre **PrivateAssemblies** et **PublicAssemblies** est que les assemblys dans **PublicAssemblies** sont énumérés dans le **Ajouter des références** boîte de dialogue. Si vous choisissez de ne pas utiliser la technique « répertoire d’installation CodeBase\/privée », vous devez installer dans le **PrivateAssemblies** active.|  
|Utiliser un assembly avec nom fort et la clé de Registre d’Assembly.|La clé de l’Assembly peut être utilisée pour indiquer explicitement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour charger un fort nommé VSPackage assembly. La valeur de la clé doit être le nom fort de l’assembly.|  
|Placez le DLL dans le **PublicAssemblies** active.|Enfin, l’assembly peut également être placé dans le **PublicAssemblies** sous\-répertoire. Assemblys situés dans **PublicAssemblies** sont détectées automatiquement et apparaît également dans le **Ajouter des références** boîte de dialogue de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Les assemblys VSPackage doivent uniquement être placés dans le **PublicAssemblies** directory s’ils contiennent les composants qui sont destinés à être réutilisé par d’autres développeurs VSPackage gérés. La majorité des assemblys ne répondent pas à ce critère.|  
  
> [!NOTE]
>  Utiliser des assemblys avec nom fort, signés pour tous vos assemblys dépendants. Ces assemblys doivent également être installés dans votre propre répertoire ou dans le global assembly cache \(GAC\). Cela empêche les conflits avec les assemblys qui ont le même nom de fichier de base, appelé liaison de nom de faible.