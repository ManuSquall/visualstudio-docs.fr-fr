---
title: "Sp&#233;cification des gestionnaires de fichiers pour les Extensions de nom de fichier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extensions de fichier, en spécifiant des gestionnaires de fichiers"
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Sp&#233;cification des gestionnaires de fichiers pour les Extensions de nom de fichier
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il existe plusieurs façons de déterminer l’application qui gère un fichier ayant une extension de fichier particulière. Les verbes OpenWithList et OpenWithProgids sont deux façons de spécifier des gestionnaires de fichiers sous l’entrée de Registre pour l’extension de fichier.  
  
## OpenWithList verbe  
 Lorsque vous cliquez sur un fichier dans l’Explorateur Windows, vous voyez les **Open** commande. Si plus d’un produit est associé à une extension, vous voyez un **Ouvrir avec** sous\-menu.  
  
 Vous pouvez enregistrer différentes applications pour ouvrir une extension en définissant la clé OpenWithList pour l’extension de fichier dans HKEY\_CLASSES\_ROOT. Les applications répertoriées sous cette clé pour une extension de fichier s’affichent sous le **programmes recommandés** titre dans le **Ouvrir avec** boîte de dialogue. L’exemple suivant montre les applications enregistrées pour ouvrir l’extension de fichier .vcproj.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Les clés spécifiant les applications sont dans la liste sous HKEY\_CLASSES\_ROOT\\Applications.  
  
 Ajout d’une clé de OpenWithList, vous déclarez que votre application prend en charge une extension de fichier même si une autre application prend possession de l’extension. Cela peut être une future version de votre application ou une autre application.  
  
## OpenWithProgIDs  
 Identificateurs de programme \(ProgID\) sont des versions conviviales de ClassID qui identifient la version d’une application ou d’un objet COM. Chaque objet qui peut être créé conjointement doit avoir son propre ProgID. Par exemple, VisualStudio.DTE.7.1 démarre Visual Studio .NET 2003 pendant le démarrage de VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En tant que propriétaire d’un type de projet ou d’un type d’élément de projet, vous devez créer un ProgID spécifique à la version de votre extension de fichier. Ces ProgID peuvent être redondants dans la mesure où plusieurs ProgID peut démarrer la même application. Pour plus d'informations, consultez [Inscription des verbes pour les Extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Utilisez la convention d’affectation de noms suivante pour le fichier version ProgID pour éviter la duplication lors de l’enregistrement d’autres fournisseurs :  
  
|Extension de fichier|Version ProgID|  
|--------------------------|--------------------|  
|.extension|ProductName. extension.versionMajor.versionMinor|  
  
 Vous pouvez enregistrer différentes applications qui sont en mesure d’ouvrir une extension de fichier particulière en ajoutant des ProgID avec version sous forme de valeurs à la HKEY\_CLASSES\_ROOT\\*\< extension \>*\\OpenWithProgids clé. Cette clé de Registre contient une liste de ProgID autres associés à l’extension de fichier. Les applications associées avec les ProgID répertoriés s’affichent dans le **Ouvrir avec***nom de produit* sous\-menu. Si la même application est spécifiée à la fois dans le `OpenWithList` et `OpenWithProgids` clés, le système d’exploitation fusionne les doublons.  
  
> [!NOTE]
>  Le `OpenWithProgids` clé est uniquement pris en charge dans Windows XP. Étant donné que les autres systèmes d’exploitation ignorer cette clé, ne l’utilisez pas que l’enregistrement uniquement pour les gestionnaires de fichiers. Cette clé permet de fournir une meilleure expérience utilisateur dans Windows XP.  
  
 Ajoutez les ProgID souhaitées en tant que valeurs de type REG\_NONE. Le code suivant fournit un exemple d’inscription ProgID pour une extension de fichier \(.*ext*\).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Le ProgID spécifié comme la valeur par défaut pour l’extension de fichier est le Gestionnaire de fichier par défaut. Si vous modifiez le ProgID pour une extension de fichier fourni avec une version précédente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou qui peut être pris en charge par d’autres applications, puis vous devez inscrire le `OpenWithProgids` pour votre extension de fichier de clé et spécifier le nouveau ProgID dans la liste, ainsi que les anciens ProgID pris en charge. Exemple :  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Si l’ancien ProgID a verbes associés, ces verbes apparaissent également sous **Ouvrir avec** *nom de produit* dans le menu contextuel.  
  
## Voir aussi  
 [À propos des Extensions de nom de fichier](../extensibility/about-file-name-extensions.md)   
 [Inscription des verbes pour les Extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)