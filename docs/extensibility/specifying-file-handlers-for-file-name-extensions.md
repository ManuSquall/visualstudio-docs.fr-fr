---
title: Spécification des gestionnaires de fichiers pour les Extensions de nom de fichier | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d0086f8badb32431c85f16e1f74fe8f186c9b2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Spécification des gestionnaires de fichiers pour les Extensions de nom de fichier
Il existe plusieurs façons de déterminer l’application qui gère un fichier qui a une extension de fichier particulier. Les verbes OpenWithList et OpenWithProgids sont deux façons de spécifier des gestionnaires de fichiers sous l’entrée de Registre pour l’extension de fichier.  
  
## <a name="openwithlist-verb"></a>OpenWithList verbe  
 Lorsque vous cliquez sur un fichier dans l’Explorateur Windows, vous voyez le **ouvrir** commande. Si plus d’un produit est associé à une extension, vous voyez un **ouvrir avec** sous-menu.  
  
 Vous pouvez enregistrer différentes applications pour ouvrir une extension en définissant la clé OpenWithList pour l’extension de fichier dans HKEY_CLASSES_ROOT. Les applications répertoriées sous cette clé pour une extension de fichier apparaissent sous le **programmes recommandés** titre dans le **ouvrir avec** boîte de dialogue. L’exemple suivant montre les applications inscrites pour ouvrir l’extension de fichier .vcproj.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Les clés spécifiant les applications sont dans la liste sous HKEY_CLASSES_ROOT\Applications.  
  
 En ajoutant une clé OpenWithList, vous déclarez que votre application prend en charge une extension de fichier même si une autre application prend possession de l’extension. Cela peut être une future version de votre application ou une autre application.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Identificateurs de programme (ProgID) sont des versions conviviales de ClassID qui identifient la version d’une application ou d’un objet COM. Chaque objet peut être créé conjointement doit avoir son propre ProgID. Par exemple, VisualStudio.DTE.7.1 démarre Visual Studio .NET 2003 pendant le démarrage de VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Comme le propriétaire d’un type de projet ou d’un type d’élément de projet, vous devez créer un ProgID spécifique à la version de votre extension de fichier. Les ProgID peuvent être redondant dans la mesure où plusieurs ProgID peut démarrer la même application. Pour plus d’informations, consultez [l’inscription des verbes pour les Extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Utilisez la convention d’affectation de noms suivante pour le fichier de contrôle de version du ProgID pour éviter la duplication avec l’enregistrement à partir d’autres fournisseurs :  
  
|Extension de fichier|Contrôle de version du ProgID|  
|--------------------|----------------------|  
|.extension|ProductName. extension.versionMajor.versionMinor|  
  
 Vous pouvez enregistrer différentes applications qui sont en mesure d’ouvrir une extension de fichier particulière en ajoutant des ProgID avec version sous forme de valeurs à la HKEY_CLASSES_ROOT\\*\<extension >*\OpenWithProgids clé. Cette clé de Registre contient une liste de ProgID autre associés à l’extension de fichier. Les applications associées avec les ProgID répertoriées apparaissent dans le **ouvrir avec *** Product Name* sous-menu. Si la même application est spécifiée à la fois dans le `OpenWithList` et `OpenWithProgids` clés, le système d’exploitation fusionne les doublons.  
  
> [!NOTE]
>  Le `OpenWithProgids` clé est uniquement pris en charge dans Windows XP. Étant donné que les autres systèmes d’exploitation ignorer cette clé, ne l’utilisez pas que l’enregistrement uniquement pour les gestionnaires de fichiers. Cette clé permet de fournir une meilleure expérience utilisateur dans Windows XP.  
  
 Ajoutez les ProgID souhaitées sous forme de valeurs de type REG_NONE. Le code suivant fournit un exemple d’inscription ProgID pour une extension de fichier (. *Ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Le ProgID spécifié comme la valeur par défaut pour l’extension de fichier est le Gestionnaire de fichier par défaut. Si vous modifiez le ProgID d’une extension de fichier fourni avec une version antérieure de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou qui peut être pris en charge par d’autres applications, puis vous devez inscrire le `OpenWithProgids` pour votre extension de fichier de clé et de spécifier le nouveau ProgID dans la liste avec les ProgID ancienne que prise en charge. Par exemple :  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Si l’ancien ProgID a verbes associés, ces verbes apparaissent également sous **ouvrir avec** *Product Name* dans le menu contextuel.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des Extensions de nom de fichier](../extensibility/about-file-name-extensions.md)   
 [Inscription des verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)