---
title: Déploiement de solutions De dépanneur Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de036ce9b0b566a6028b0ccfe45cfe5f2ac49da9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444932"
---
# <a name="troubleshoot-office-solution-deployment"></a>Déploiement de solutions De dépanneur Office
  Cette rubrique contient des informations sur la résolution des problèmes courants que vous pouvez rencontrer lorsque vous déployez des solutions Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Solutions De bureau de dépannage en utilisant le visualiseur d’événements
 Vous pouvez utiliser l’observateur d’événements de Windows pour consulter les messages d’erreur capturés par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] lors de l’installation ou de la désinstallation de solutions Office. Vous pouvez utiliser ces messages du journal des événements pour résoudre les problèmes d’installation et de déploiement. Pour plus d’informations, voir [Event logging for Office solutions](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Changer le nom de l’assemblage provoque des conflits
 Si vous modifiez la valeur **du nom d’assemblage** dans la page **d’application** du concepteur de **projet** après avoir déjà déployé une solution, les outils de publication modifieront le package Setup pour avoir un fichier *Setup.exe* et deux manifestes de déploiement. Si vous déployez deux fichiers manifeste, les conditions suivantes peuvent se produire :

- Si l’utilisateur final installe les deux versions, l’application charge les deux compléments VSTO.

- Si le complément VSTO a été installé avant que le nom de l’assembly ait été modifié, l’utilisateur final ne recevra jamais des mises à jour.

  Pour éviter ces conditions, ne modifiez pas la valeur du **nom d’assemblage** de la solution après le déploiement de la solution.

## <a name="check-for-updates-takes-a-long-time"></a>Vérifier les mises à jour prend beaucoup de temps
 Visual Studio 2010 Tools for Office runtime fournit une inscription au registre que les administrateurs peuvent utiliser pour définir la valeur de temps d’arrêt pour le téléchargement des manifestes et de la solution.

#### <a name="to-set-the-time-out-value"></a>Pour définir la valeur du délai d’attente

1. Dans le Registre, accédez à la clé suivante :

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. Dans la sous-clé **AddInTimeout** , définissez la valeur du délai d’attente en millisecondes.

     Si la sous-clé **AddInTimeout** n’existe pas, créez-la comme valeur DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Impossible de mettre à jour ou de publier sur une part de fichier réseau
 Les solutions de bureau qui sont sur une part de fichier réseau peuvent afficher un message trompeur pendant les mises à jour si le fichier *Setup.exe* de la solution est verrouillé dans un processus pendant la publication de la mise à jour. Le message suivant peut s’afficher : « Impossible d’ajouter 'setup.exe' au site web. Le fichier 'setup.exe' existe déjà dans le site web. »

 Pour empêcher le verrouillage du fichier, vous pouvez activer le partage en lecture seule pour les utilisateurs finaux. Toutefois, si les documents sont sur le partage, ils sont également activés en lecture seule pour les utilisateurs finaux.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Les conditions préalables pour Microsoft Office ne sont pas installées
 Vous pouvez ajouter le .NET Framework, la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]et les assemblys PIA (Primary Interop Assembly) Office à votre package d’installation comme composants requis déployés avec votre solution Office. Pour plus d’informations sur la façon d’installer les principaux assemblages interop, voir [Configurer un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) et [Comment: Installer des assemblages interop primaires De Bureau](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Publier à l’aide de Localhost peut causer des problèmes d’installation
 Lorsque vous `http://localhost` utilisez comme emplacement de publication ou d’installation pour des solutions au niveau de document, le **Assistant Publier** ne convertit pas la chaîne au vrai nom de l’ordinateur. Dans ce cas, la solution doit être installée sur l’ordinateur de développement. Pour que des solutions déployées utilisent IIS sur l’ordinateur de développement, utilisez le nom complet pour tous les emplacements HTTP/HTTPS/FTP au lieu de localhost.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Les assemblages en cache sont chargés au lieu d’assemblages mis à jour
 Fusion, le chargeur d’assembly .Net Framework, charge la copie mise en cache des assemblys lorsque le chemin de sortie du projet est sur un partage de fichiers réseau, que l’assembly est signé avec un nom fort et que la version d’assembly de la personnalisation ne change pas. Si vous mettez à jour un assembly qui satisfait ces conditions, la mise à jour ne s’affiche pas lors de la prochaine exécution du projet, car la copie mise en cache est chargée.

 Vous pouvez configurer Visual Studio pour que Fusion télécharge les assemblys chaque fois que le projet est exécuté.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Pour télécharger des assemblys au lieu de charger des copies mises en cache

1. Dans la barre de menus, choisissez **Projet**, _Propriétés de_**NomProjet**.

2. Dans la page **Application** , choisissez **Informations de l’assembly**.

3. Définissez le numéro de révision, troisième champ, de\*la **version d’assemblage**, à une wild card ( ). Par exemple, "1.0".  Ensuite, choisissez le bouton **OK.**

   Après avoir modifié la version d’assembly, vous pouvez continuer à signer votre assembly avec un nom fort, et Fusion chargera la version de la personnalisation.

 [!NOTE]
> En commençant par Visual Studio 2017, si vous essayez d’utiliser des wild cards dans la version Assembly, une erreur de construction se produira.  C’est parce que les wild cards dans la version d’assemblage brisera la fonction déterministe MSBuild. Vous serez chargé soit de supprimer les wildcards de la version d’assemblage, ou de désactiver le déterminisme.  Pour en savoir plus sur la fonction déterministe voir: [Propriétés du projet MSBuild commune](../msbuild/common-msbuild-project-properties.md) et [personnaliser votre build](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>L’installation échoue lorsque l’URI a des caractères qui ne sont pas US-ASCII
 Lorsque vous publiez une solution Office sur un emplacement HTTP/HTTPS/FTP, le chemin d’accès ne peut contenir aucun caractère Unicode qui ne sont pas en US-ASCII. Ces caractères peuvent provoquer un comportement anormal dans le programme d’installation. Utilisez des caractères US-ASCII pour le chemin d’installation.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Prompt to manually uninstall apparaît lorsque vous publiez et installez une solution sur l’ordinateur de développement
 Lorsque vous générez une solution Office, la version créée est inscrite automatiquement. Si vous avez déjà publié et installé la même solution sur votre ordinateur de développement, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] détecte que le chemin d’installation de la version publiée et celui de la version générée sont différents après la génération, la régénération et la publication de l’application. Le message d’erreur suivant s’affiche : « La personnalisation ne peut pas être installée car une autre version est actuellement installée et ne peut pas être mis à niveau depuis cet emplacement. » Les clés de Registre sont mises à jour chaque fois qu’une solution est régénérée. Par conséquent, vous devez désinstaller la version précédente avant de publier, de déboguer ou d’exécuter la nouvelle version.

 Pour empêcher l’affichage de ce message, créez un autre compte d’utilisateur sur votre ordinateur de développement pour tester votre déploiement. Vous pouvez également désinstaller la version de la liste des programmes installés sur l’ordinateur avant de publier, de déboguer ou de régénérer ensuite la solution.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Exception ou méthode non constatée lorsque vous installez une solution
 Lorsque vous installez des solutions Office en ouvrant le manifeste de déploiement (un fichier *.vsto),* l’application Bureau, le document ou le cahier de travail, des messages d’erreur pour les conditions suivantes peuvent apparaître :

- Méthode introuvable.

- MissingMethodException.

- Exception non interceptée.

  Pour que ces messages d’erreur ne s’affichent pas, installez la solution en exécutant le programme d’installation.

  Lorsque vous installez la solution sans exécuter le programme d’installation, celui-ci ne recherche pas ou n’installe pas les composants requis. Le programme d’installation vérifie si la version des composants requis est correcte et les installe si nécessaire.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Les clés de registre manifeste pour les add-ins changent après la construction d’un projet InstallShield Limited Edition
 La clé de registre manifeste qui fait partie d’un programme d’installation supplémentaire VSTO passe parfois de *.vsto* à *.dll.manifest* lorsque vous construisez un projet InstallShield Limited Edition.

 Pour contourner ce problème, créez le projet InstallShield Limited Edition dans une autre solution ou utilisez CompanyName.AddinName comme valeur de la clé de Registre qui contient le nom du complément VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>L’installateur ClickOnce pour votre solution Office n’installe pas les principaux assemblages interop
 Lorsque vous exécutez le programme d’installation que ClickOnce crée pour votre solution Office, le programme d’installation des assemblys PIA (Primary Interop Assemblies) Office s’exécute uniquement si aucun assembly PIA n’est déjà installé.

 Si le programme Setup n’installe pas correctement les API, installez-les manuellement en exécutant le fichier d’installateur qui s’appelle *o2007pia.msi* à partir du répertoire d’installation.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Les solutions Reinstall Office suscitent un argument hors de portée
 Lorsque vous réinstallez une solution Office, une exception <xref:System.ArgumentOutOfRangeException> peut s’afficher avec le message d’erreur suivant : « L’argument spécifié n’était pas dans les limites de la plage des valeurs valides. »

 Cette situation se produit si la casse de l’URL de l’emplacement d’installation est différente. Par exemple, cette erreur apparaîtrait si `http://fabrikam.com/ExcelSolution.vsto` vous avez installé `http://fabrikam.com/excelsolution.vsto` une solution Office dès la première fois et que vous avez ensuite utilisé la deuxième fois.

 Pour empêcher l’affichage de ce message, utilisez la même casse lorsque vous installez des solutions Office.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Impossible d’installer une solution ClickOnce en ouvrant le manifeste de déploiement à partir du web
 Les utilisateurs peuvent installer des solutions Office en ouvrant le manifeste de déploiement à partir du web. Cependant, certaines installations des Services d’information Internet (IIS) bloquent l’extension du nom de fichier *.vsto.* Vous devez définir le type MIME dans l’IIS avant de l’utiliser pour déployer une solution Office.

 Pour plus d’informations sur la façon de définir le type MIME dans IIS 7, voir [Ajouter un type MIME (IIS7)](https://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Définissez l’extension sur **.vsto** et le type MIME sur **application/x-ms-vsto**.

## <a name="see-also"></a>Voir aussi

- [Dépanner des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
