---
title: Réparer Visual Studio
titleSuffix: ''
description: Découvrez comment réparer une installation de Visual Studio 2017.
ms.date: 06/15/2020
ms.custom: seodec18
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fda72206059e5c14c46d332e44ea0de481004296
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85418962"
---
# <a name="repair-visual-studio"></a>Réparer Visual Studio

Il peut arriver que votre installation Visual Studio soit endommagée ou corrompue. Une réparation est utile pour résoudre les problèmes d’installation dans toutes les opérations d’installation, y compris les mises à jour.

## <a name="when-to-use-repair"></a>Quand utiliser la réparation
* Si vous rencontrez des problèmes de charge utile d’installation. Cela peut se produire lorsque l’écriture du fichier sur le disque échoue et ne peut pas être corrigée en supprimant le fichier endommagé. La réparation peut acquérir à nouveau les fichiers nécessaires. 
* Si vous rencontrez des problèmes de téléchargement côté client. En supposant que vous avez résolu les problèmes de connexion ou de proxy, la réparation peut être utile. 
* Si vous rencontrez des problèmes de mise à jour de Visual Studio. La réparation corrige de nombreux problèmes de mise à jour courants. 

> [!TIP] 
> Si le problème d’installation est dû à un problème dans un service Windows sous-jacent, comme Windows Installer, la réparation peut être à l’origine du problème. Les problèmes système peuvent inclure une Windows Installer rompue ou une connexion Internet instable. Pour vérifier s’il s’agit d’un problème système, utilisez le rapport d’erreurs généré à partir de l’opération d’installation.

> [!NOTE] 
> La réparation de Visual Studio réinitialise les paramètres utilisateur, puis réinstalle les assemblys que vous avez déjà. Si vous rencontrez un problème de produit, créez un [ticket de commentaires Visual Studio](https://developercommunity.visualstudio.com/content/problem/post.html?space=8), car la réparation peut ne pas résoudre le problème.

## <a name="how-to-repair"></a>Réparation
::: moniker range="vs-2017"

1. Recherchez le **programme d’installation de Visual Studio** sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant la Mise à jour anniversaire Windows 10 ou une version ultérieure, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** pour l’afficher comme **Visual Studio Installer**.

   > [!NOTE]
   > Sur certains ordinateurs, le programme d’installation de Visual Studio peut être répertorié sous la lettre **« M »** comme **Microsoft, programme d’installation de Visual Studio**.
   >
   > Ou bien, vous pouvez trouver Visual Studio Installer à l’emplacement suivant :`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Dans le programme d’installation, choisissez **Plus**, puis choisissez **Réparer**.

    ![Réparez Visual Studio à partir de l’Visual Studio Installer](media/repair-visual-studio.png "Réparez Visual Studio à partir de l’Visual Studio Installer")

   > [!NOTE]
   > La réparation de Visual Studio réinitialisera l’environnement. Les personnalisations locales comme les extensions par utilisateur installées sans élévation, les paramètres utilisateurs et les profils seront supprimées. Vos paramètres synchronisés tels que les thèmes, les couleurs et les combinaisons de touches seront restaurés.
   >

   > [!TIP]
   > L’option **Réparer** n’apparaît que pour les instances installées de Visual Studio. Si vous ne voyez pas l’option **Réparer**, c’est sans doute que vous avez sélectionné **Plus** dans une version présentée comme « Disponible » et non « Installé » dans Visual Studio Installer.

::: moniker-end

::: moniker range="vs-2019"

1. Recherchez le **programme d’installation de Visual Studio** sur votre ordinateur.

     Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

     ![Ouvrez le Visual Studio Installer](media/vs-2019/vs-installer-windows-start.png "Ouvrez le Visual Studio Installer")

     > [!NOTE]
     > Vous trouverez également Visual Studio Installer à l’emplacement suivant :
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio que vous avez installée. Cliquez ensuite sur **Plus**, puis choisissez **Réparer**.

     ![Réparer Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Réparer Visual Studio 2019")

   > [!NOTE]
   > La réparation de Visual Studio réinitialisera l’environnement. Les personnalisations locales comme les extensions par utilisateur installées sans élévation, les paramètres utilisateurs et les profils seront supprimées. Vos paramètres synchronisés tels que les thèmes, les couleurs et les combinaisons de touches seront restaurés.
   >

   > [!TIP]
   > L’option **Réparer** n’apparaît que pour les instances installées de Visual Studio. Si vous ne voyez pas l’option **Réparer**, c’est sans doute que vous avez sélectionné **Plus** dans une version présentée comme « Disponible » et non « Installé » dans Visual Studio Installer.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)
* [Résolution des problèmes d’installation et de mise à niveau de Visual Studio](troubleshooting-installation-issues.md)
