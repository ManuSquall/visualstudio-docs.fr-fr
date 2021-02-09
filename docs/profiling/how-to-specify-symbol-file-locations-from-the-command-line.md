---
title: Spécifier les emplacements des fichiers de symboles à partir de la ligne de commande
description: Découvrez comment l’outil en ligne de commande VSPerfReport requiert l’accès aux fichiers de symboles (. pdb) pour afficher des informations de symbole telles que les noms de fonctions et les numéros de ligne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1ea3eff001c49f4d7546985f1357126dc87717bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920719"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Guide pratique pour spécifier les emplacements du fichier de symboles à partir de la ligne de commande
Pour pouvoir afficher des informations de symboles telles que les noms de fonctions et les numéros de ligne, l’outil en ligne de commande VSPerfReport nécessite l’accès aux fichiers de symboles (.*pdb*) des composants profilés, ainsi qu’aux fichiers système Windows. Les fichiers de symboles sont créés lors de la compilation d’un composant. Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport recherche automatiquement les fichiers de symboles dans les emplacements suivants :

- Chemins spécifiés dans l’option **/SymbolPath** ou dans la variable d’environnement **_NT_SYMBOL_PATH**.

- Chemin local exact dans lequel un composant a été compilé.

- Répertoire contenant le fichier de données de profilage (fichier .*vsp* ou .*vsps*).

  Microsoft fournit les fichiers .*pdb* d’un grand nombre de ses produits en ligne sur un serveur de symboles. Si l’ordinateur que vous utilisez pour la génération de rapports est connecté à Internet, VSPerfReport se connecte au serveur de symboles en ligne afin de rechercher automatiquement les informations de symboles et d’enregistrer les fichiers dans un magasin local.

  Vous pouvez spécifier l’emplacement des fichiers de symboles et de la banque de serveurs de symboles Microsoft en procédant de l’une des manières suivantes :

- Définissez la variable d’environnement **_NT_SYMBOL_PATH**.

- Ajoutez l’option **/SymbolPath** à la ligne de commande de VSPerfReport.

  Vous pouvez également combiner ces deux méthodes.

> [!NOTE]
> Si [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est installé sur l’ordinateur local, un emplacement pour les fichiers de symboles Windows a probablement déjà été défini. Pour plus d’informations, consultez [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md). Vous devez toujours configurer VSPerfReport pour utiliser l’emplacement et le serveur comme décrit plus loin dans cette rubrique.

## <a name="specify-windows-symbol-files"></a>Spécifier des fichiers de symboles Windows

#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Pour configurer l’utilisation du serveur de symboles Windows

1. Si nécessaire, créez un répertoire dans lequel stocker les fichiers de symboles localement.

2. Utilisez la syntaxe suivante pour définir la variable d’environnement **_NT_SYMBOL_PATH** ou l’option VSPerfReport /SymbolPath :

    `srv*<LocalStore>*https://msdl.microsoft.com/download/symbols`

    où *<LocalStore>* est le chemin d’accès du répertoire local que vous avez créé.

## <a name="specify-component-symbol-files"></a>Spécifier des fichiers de symboles de composants
 Les Outils de profilage recherchent les fichiers .*pdb* des composants que vous souhaitez profiler dans leurs emplacements d’origine, qui sont stockés dans les composants ou dans le dossier contenant le fichier de données de profilage. Vous pouvez spécifier d’autres emplacements dans lesquels effectuer la recherche en ajoutant un ou plusieurs chemins à **_NT_SYMBOL_PATH** ou à l’option **/SymbolPath**. Séparez les chemins par des points-virgules.

## <a name="example"></a>Exemple
 La ligne de commande suivante définit le serveur de symboles Windows comme valeur de la variable d’environnement **_NT_SYMBOL_PATH** et **C:\Symbols** comme répertoire local.

 ```cmd
  set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/download/symbols
 ```

 La ligne de commande VSPerfReport suivante ajoute le répertoire *C:\Projects\Symbols* au chemin de recherche à l’aide de l’option **/SymbolPath** .

 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**
