---
title: Spécification de gestionnaires de fichiers pour les extensions de nom de fichier | Microsoft Docs
description: Découvrez comment déterminer quelle application gère une extension de fichier dans le kit de développement logiciel (SDK) Visual Studio à l’aide de OpenWithList et OpenWithProgids.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ab370b4be8c12ad0df0c4822bcc7b487fb4aa21
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899444"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Spécification des gestionnaires de fichiers pour les extensions de nom de fichier
Il existe plusieurs façons de déterminer l’application qui gère un fichier qui a une extension de fichier particulière. Les verbes OpenWithList et OpenWithProgids sont deux façons de spécifier des gestionnaires de fichiers sous l’entrée de Registre pour l’extension de fichier.

## <a name="openwithlist-verb"></a>Verbe OpenWithList
 Lorsque vous cliquez avec le bouton droit sur un fichier dans l’Explorateur Windows, la commande **ouvrir** s’affiche. Si plusieurs produits sont associés à une extension, vous voyez s’afficher un sous-menu **Ouvrir avec** .

 Vous pouvez inscrire différentes applications pour ouvrir une extension en définissant la clé OpenWithList pour l’extension de fichier dans HKEY_CLASSES_ROOT. Les applications répertoriées sous cette clé pour une extension de fichier apparaissent sous l’en-tête **Programmes recommandés** dans la boîte de dialogue **Ouvrir avec** . L’exemple suivant montre les applications inscrites pour ouvrir l’extension de fichier. vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Les clés qui spécifient les applications figurent dans la liste sous HKEY_CLASSES_ROOT\Applications.

 En ajoutant une clé OpenWithList, vous déclarez que votre application prend en charge une extension de fichier même si une autre application prend possession de l’extension. Il peut s’agir d’une version ultérieure de votre application ou d’une autre application.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Les identificateurs programmatiques (ProgID) sont des versions conviviales de ClassID qui identifient une version d’une application ou d’un objet COM. Chaque objet CoCreatable doit avoir son propre ProgID. Par exemple, VisualStudio. DTE. 7.1 démarre Visual Studio .NET 2003 pendant le démarrage de VisualStudio. DTE. 10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . En tant que propriétaire d’un type de projet ou d’élément de projet, vous devez créer un ProgID spécifique à la version pour votre extension de fichier. Ces ProgID peuvent être redondants dans le risque que plusieurs ProgID démarrent la même application. Pour plus d’informations, consultez [inscription de verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md).

 Utilisez la Convention d’affectation de noms suivante pour les ProgID de fichier avec version pour éviter la duplication avec l’inscription d’autres fournisseurs :

|Extension de fichier|ProgID avec version|
|--------------------|----------------------|
|. extension|ProductName. extension. versionMajor. versionMinor|

 Vous pouvez inscrire différentes applications capables d’ouvrir une extension de fichier particulière en ajoutant des ProgID avec version comme valeurs à la \\ *\<extension>* clé HKEY_CLASSES_ROOT \OpenWithProgids. Cette clé de registre contient une liste d’autres ProgID associés à l’extension de fichier. Les applications associées aux ProgID répertoriés s’affichent dans le sous-menu **Ouvrir avec** le _nom de produit_ . Si la même application est spécifiée dans les deux `OpenWithList` `OpenWithProgids` clés et, le système d’exploitation fusionne les doublons.

> [!NOTE]
> La `OpenWithProgids` clé est uniquement prise en charge dans Windows XP. Étant donné que les autres systèmes d’exploitation ignorent cette clé, ne l’utilisez pas comme seule inscription pour les gestionnaires de fichiers. Utilisez cette clé pour offrir une meilleure expérience utilisateur dans Windows XP.

 Ajoutez les ProgID souhaités en tant que valeurs de type REG_NONE. Le code suivant fournit un exemple d’inscription de ProgID pour une extension de fichier (.*ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Le ProgID spécifié comme valeur par défaut pour l’extension de fichier est le gestionnaire de fichiers par défaut. Si vous modifiez le ProgID pour une extension de fichier fournie avec une version précédente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou qui peut être prise en charge par d’autres applications, vous devez inscrire la `OpenWithProgids` clé pour votre extension de fichier et spécifier le nouveau ProgID dans la liste avec les anciens ProgID pris en charge. Par exemple :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Si l’ancien ProgID est associé à des verbes, ces verbes s’affichent **également sous le** *nom du produit* dans le menu contextuel.

## <a name="see-also"></a>Voir aussi
- [À propos des extensions de nom de fichier](../extensibility/about-file-name-extensions.md)
- [Inscription des verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)
