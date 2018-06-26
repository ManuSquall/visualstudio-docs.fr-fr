---
title: Remplacements dans Help Content Manager
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a02f4af740910fe666af295aa8535c8aef8245c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571736"
---
# <a name="help-content-manager-overrides"></a>Remplacements dans Help Content Manager

Vous pouvez changer le comportement par défaut de Help Viewer et des fonctionnalités d’aide dans l’IDE Visual Studio. Certaines options peuvent être spécifiées en créant un fichier [.pkgdef](https://blogs.msdn.microsoft.com/visualstudio/2009/12/18/whats-a-pkgdef-and-why/) pour définir différentes valeurs de clé de Registre. D’autres sont définies directement dans le Registre.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Comment contrôler le comportement de Help Viewer à l’aide d’un fichier .pkgdef

1. Créez un fichier *.pkgdef* avec `[$RootKey$\Help]` comme première ligne.

2. Ajoutez l’une des valeurs de clé de Registre ou la totalité des valeurs décrites dans le tableau ci-dessous sur des lignes distinctes, par exemple `"UseOnlineHelp"=dword:00000001`.

3. Copiez le fichier dans *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<édition\>\Common7\IDE\CommonExtensions*.

4. Exécutez `devenv /updateconfiguration` dans une invite de commandes développeur.

### <a name="registry-key-values"></a>Valeurs de la clé de Registre

|Valeur de la clé de Registre|Type|Données|Description|
|------------------|----|----|-----------|
|NewContentAndUpdateService|chaîne|\<URL HTTP du point de terminaison de service\>|Définir un point de terminaison de service unique|
|UseOnlineHelp|dword|`0` pour spécifier l’aide locale, `1` pour spécifier l’aide en ligne|Définir l’aide en ligne ou l’aide locale comme option par défaut|
|OnlineBaseUrl|chaîne|\<URL HTTP du point de terminaison de service\>|Définir un point de terminaison unique F1|
|OnlineHelpPreferenceDisabled|dword|`0` pour activer ou `1` pour désactiver l’option de préférence d’aide en ligne|Désactiver l’option de préférence d’aide en ligne|
|DisableManageContent|dword|`0` pour activer ou `1` pour désactiver l’onglet **Gérer le contenu** dans Help Viewer|Désactiver l’onglet **Gérer le contenu**|
|DisableFirstRunHelpSelection|dword|`0` pour activer ou `1` pour désactiver les fonctionnalités d’aide configurées au premier démarrage de Visual Studio.|Désactiver l’installation du contenu au premier démarrage de Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Exemple de contenu de fichier .pkgdef

```
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Utiliser l’Éditeur du Registre pour modifier le comportement de l’application Help Viewer

Les deux comportements suivants peuvent être contrôlés en définissant des valeurs de clé de Registre dans l’Éditeur du Registre.

|Tâche|Clé de Registre|Value|Données|
|----------|-----|------|----|
|Substituer la priorité des travaux BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (sur un ordinateur 64 bits)\Microsoft\Help\v2.3|BITSPriority|**premier plan**, **haute**, **normale** ou **faible**|
|Pointer vers le magasin de contenu local sur un partage réseau|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Voir aussi

- [Guide de l’administrateur Help Viewer](../ide/help-viewer-administrator-guide.md)
- [Arguments de ligne de commande pour Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md)
- [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)