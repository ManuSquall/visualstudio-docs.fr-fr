---
title: Spécifier les gestionnaires de fichiers pour les extensions de nom de fichier (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699752"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Spécification des gestionnaires de fichiers pour les extensions de nom de fichier
Il existe un certain nombre de façons de déterminer l’application qui gère un fichier qui a une extension de fichier particulière. Les verbes OpenWithList et OpenWithProgids sont deux façons de spécifier les gestionnaires de fichiers sous l’entrée du registre pour l’extension du fichier.

## <a name="openwithlist-verb"></a>Verbe OpenWithList
 Lorsque vous cliquez à droite sur un fichier dans Windows Explorer, vous voyez la commande **Open.** Si plus d’un produit est associé à une extension, vous voyez un **Open With** submenu.

 Vous pouvez enregistrer différentes applications pour ouvrir une extension en définissant la clé OpenWithList pour l’extension de fichiers dans HKEY_CLASSES_ROOT. Les applications énumérées sous cette clé pour une extension de fichier apparaissent sous la rubrique **Programmes Recommandés** dans la boîte de dialogue **Open With.** L’exemple suivant montre les applications enregistrées pour ouvrir l’extension du fichier .vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Les clés spécifiant les applications proviennent de la liste dans HKEY_CLASSES_ROOT-Applications.

 En ajoutant une clé OpenWithList, vous déclarez que votre application prend en charge une extension de fichier même si une autre application prend possession de l’extension. Il peut s’agir d’une future version de votre application ou d’une autre application.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Les identificateurs programmatiques (ProgID) sont des versions amicales de ClassIDs qui identifient une version d’une application ou d’un objet COM. Chaque objet co-creatable doit avoir son propre ProgID. Par exemple, VisualStudio.DTE.7.1 démarre Visual Studio .NET 2003 tandis que VisualStudio.DTE.10.0 commence [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En tant que propriétaire d’un type de projet ou d’un type d’élément de projet, vous devez créer un ProgID spécifique à la version pour votre extension de fichiers. Ces ProgID peuvent être redondants en ce que plus d’un ProgID peut démarrer la même application. Pour plus d’informations, voir [Enregistrement des verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md).

 Utilisez la convention de nommage suivante pour les ProgID de fichiers versionnés pour éviter les chevauchements avec l’enregistrement d’autres fournisseurs :

|Extension de fichier|ProgID version|
|--------------------|----------------------|
|.extension|Productname. extension.versionMajor.versionMinor|

 Vous pouvez enregistrer différentes applications qui sont en mesure d’ouvrir une extension de fichier particulière\\en ajoutant des ProgID versionnés comme valeurs à*\<l’extension HKEY_CLASSES_ROOT>*'OpenWithProgids clé. Cette clé de registre contient une liste de ProgIDs alternatifs associés à l’extension du fichier. Les applications associées aux ProgID répertoriés apparaissent dans le sous-marin **Open With**_Product Name._ Si la même application est `OpenWithList` `OpenWithProgids` spécifiée dans les deux touches et clés, le système d’exploitation fusionne les doublons.

> [!NOTE]
> La `OpenWithProgids` clé n’est pris en charge que dans Windows XP. Étant donné que d’autres systèmes d’exploitation ignorent cette clé, ne l’utilisez pas comme seule inscription pour les gestionnaires de fichiers. Utilisez cette clé pour offrir une meilleure expérience utilisateur dans Windows XP.

 Ajoutez les ProgID désirés comme valeurs du type REG_NONE. Le code suivant fournit un exemple d’enregistrement des ProgID pour une extension de fichier (.* ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Le ProgID spécifié comme la valeur par défaut pour l’extension de fichier est le gestionnaire de fichiers par défaut. Si vous modifiez le ProgID pour une extension [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de fichier qui a expédié avec une `OpenWithProgids` version précédente de ou qui peut être repris par d’autres applications, alors vous devez enregistrer la clé pour votre extension de fichier et spécifier le nouveau ProgID dans la liste avec les anciens ProgID que vous soutenez. Par exemple :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Si l’ancien ProgID a des verbes associés à elle, alors ces verbes apparaîtront également sous **Open With** *Product Name* dans le menu raccourci.

## <a name="see-also"></a>Voir aussi
- [À propos des extensions de nom de fichier](../extensibility/about-file-name-extensions.md)
- [Inscription des verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)
