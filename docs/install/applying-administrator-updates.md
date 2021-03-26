---
title: Application des mises à jour de l’administrateur à Visual Studio avec le point de terminaison Microsoft Configuration Manager
titleSuffix: ''
description: Découvrez comment appliquer les mises à jour de l’administrateur à Visual Studio.
ms.date: 03/10/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 78c2de8b1d1ffb28cc536b770bf6bd9a4ab0aa35
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2021
ms.locfileid: "105617327"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Application des mises à jour de l’administrateur qui utilisent le point de terminaison Microsoft Configuration Manager

Ce document décrit les différents types et caractéristiques des mises à jour de l’Administrateur Visual Studio. Vous trouverez ci-dessous des informations sur la manière et le moment où elles doivent être distribuées dans l’ensemble de votre organisation, sur les options de configuration disponibles et sur l’affichage des rapports et sur la résolution des problèmes. Pour plus d’informations sur les conditions préalables à l’utilisation des mises à jour de l’administrateur, consultez [activation des mises à jour](../install/enabling-administrator-updates.md)de l’administrateur.

## <a name="understanding-visual-studio-administrator-updates"></a>Fonctionnement des mises à jour de l’Administrateur Visual Studio 

Le package de mise à jour de l’Administrateur Visual Studio publié sur Microsoft Update en vue de sa consommation par le catalogue Microsoft et WSUS contient des informations que le Configuration Manager doit être en mesure de télécharger et de distribuer la mise à jour de Visual Studio sur les ordinateurs clients. Il contient également les informations dont un administrateur a besoin pour décider quelles mises à jour distribuer au sein de l’organisation et facilite la maintenance des dispositions du réseau. Les packages de mise à jour de l’Administrateur Visual Studio ne contiennent pas suffisamment d’informations pour effectuer une nouvelle installation du produit, ni contenir aucun des binaires de produit réels publiés sur le réseau de distribution de contenu. Les mises à jour de l’Administrateur Visual Studio sont cumulatives, tout comme les mises à jour standard de Visual Studio. Vous pouvez supposer que toute mise à jour de Visual Studio avec un numéro de version de produit supérieur et une date de publication ultérieure est un sur-ensemble d’une version antérieure antérieure. 

Les mises à jour de l’Administrateur Visual Studio s’appliquent aux versions de maintenance de Visual Studio qui sont prises en charge. Pour plus d’informations sur les lignes de base de maintenance de Visual Studio qui sont toujours prises en charge pendant un laps de temps donné, consultez [cycle de vie et maintenance du produit Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs). Toutes les lignes de base de maintenance de Visual Studio prises en charge restent sécurisées.  

## <a name="types-and-characteristics-of-administrator-updates"></a>Types et caractéristiques des mises à jour de l’administrateur 

Il existe trois types de mises à jour de l’administrateur pour Visual Studio :

* Les **mises à jour de sécurité** s’appliquent à toutes les éditions de Visual Studio (par exemple, entreprise, professionnel, communauté, etc.), et elles contiennent des modifications de niveau de maintenance limitées, hautement ciblées et compatibles. Les mises à jour de sécurité ne feront pas passer un client à une version mineure ultérieure ; ils sont conçus pour fournir des correctifs aux failles de sécurité d’un client qui est déjà à un niveau de version mineure particulier. Les mises à jour de sécurité comporteront au moins un correctif de sécurité, mais le correctif de sécurité peut être ou non dans un composant ou une charge de travail qui est installée sur l’ordinateur client. Par exemple, nous pourrions résoudre une faille de sécurité dans les composants .NET et nous étiqueterons la mise à jour en tant que mise à jour de sécurité, mais cela n’aurait pas vraiment d’effet significatif sur un ordinateur client sur lequel seuls les composants C++ étaient installés. Les mises à jour de sécurité peuvent également contenir d’autres correctifs de fiabilité ou d’autres mises à jour de composants nécessaires. Les mises à jour de sécurité sont publiées dans le [catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) et [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus), où elles sont classées en tant que « mises à jour de sécurité ».
 
* Les **mises à jour de fonctionnalités** permettent aux administrateurs informatiques d’étendre les ordinateurs de leur organisation à une version mineure plus récente de Visual Studio 2019. Les mises à jour de fonctionnalités s’appliquent uniquement aux éditions de Visual Studio qui se trouvent généralement dans les entreprises, telles que les références SKU d’outils d’entreprise, professionnels et de Build. Toutes les mises à jour de fonctionnalités sont publiées dans le catalogue Microsoft Update sous la forme de « packs de fonctionnalités », et elles sont disponibles pour une [importation manuelle dans Configuration Manager à partir du catalogue Microsoft Update](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog). Les mises à jour de fonctionnalités sont cumulatives et contiennent des correctifs de sécurité et de qualité supplémentaires. Consultez la [section Options de configuration](#understanding-configuration-options) ci-dessous pour obtenir des instructions sur la configuration d’un ordinateur client pour qu’il reste sur une ligne de base de maintenance et empêcher la remise des mises à jour de fonctionnalités à des clients spécifiques. 

* Les **mises à jour qualité** sont également applicables uniquement aux éditions de Visual Studio qui se trouvent généralement dans les entreprises, et elles contiennent des modifications de niveau de maintenance limitées, hautement ciblées et compatibles. Les mises à jour qualité ne feront pas passer un client à une version mineure ultérieure ; ils sont conçus pour fournir des correctifs de performances et de fiabilité, ou d’autres mises à jour de composants nécessaires à un client qui est déjà à un niveau de version mineure particulier. Les mises à jour qualité s’accumulent avec les mises à jour de sécurité et contiendront donc des correctifs de sécurité uniquement si le correctif de sécurité a déjà été publié indépendamment. Les mises à jour qualité sont publiées dans le catalogue Microsoft Update en tant que « mises à jour », et elles sont également disponibles pour une importation manuelle et facultative [dans Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog).

### <a name="decoding-the-titles-of-administrator-updates"></a>Décodage des titres des mises à jour de l’administrateur

Le titre de chaque mise à jour d’administrateur décrit la plage de versions applicable et la version résultante de la mise à jour.Par exemple,

* La **version 16.7.0 de Visual studio 2019 à 16.7.12 mise à jour** classifiée comme une « mise à jour de sécurité » s’applique à toute édition de Visual Studio sur le client entre les versions 16.7.0 à 16.7.12, et elle met à jour ces éditions clientes vers 16.7.12.  

* La **version 16.0.0 de Visual studio 2019 vers 16.9.0 mise à jour** classifiée comme un « Feature Pack » s’applique à certaines éditions de Visual Studio sur le client entre la totalité de la plage de versions de produit de 16.0.0 à 16.9.0, et elle mettra à jour ces éditions client (qui n’ont pas été configurées pour rester sur une ligne de base de maintenance antérieure) vers 16.9.0. 

* La **version 16.8.0 de Visual studio 2019 à 16.8.7 mise à jour** classée comme simple « mises à jour » s’applique à certaines éditions de Visual Studio sur le client entre les versions 16.8.0 à 16.8.7 et met à jour ces éditions clientes vers 16.8.7. 

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Utilisation de Configuration Manager pour déployer des mises à jour de Visual Studio

### <a name="understanding-configuration-options"></a>Comprendre les options de configuration

Certaines options de configuration peuvent être utilisées pour adapter les mises à jour de l’Administrateur Visual Studio afin qu’elles soient compatibles et alignées avec les exigences de déploiement de votre organisation. Les options les plus courantes sont répertoriées ci-dessous.  Pour obtenir une liste exhaustive de tous les paramètres de ligne de commande pris en charge par les mises à jour de l’administrateur, reportez-vous à la [documentation utiliser les paramètres de ligne de commande pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) et ne prêter attention qu’à ceux qui correspondent à l’action « mettre à jour ».

* **Abonnement à la mise à jour des administrateurs**: cette clé de Registre décrite dans [activation des mises à jour](../install/enabling-administrator-updates.md) de l’administrateur est requise pour que l’ordinateur client reçoive les mises à jour de l’administrateur. Il s’agit d’une clé à l’ensemble de l’ordinateur, ce qui signifie qu’elle s’applique à toutes les instances de Visual Studio installées sur la boîte. 
 
* **Désactivation du développeur**: les développeurs peuvent utiliser une clé de **AdministratorUpdatesOptOut** à l’ensemble de l’ordinateur   pour refuser de recevoir *les* mises à jour de l’Administrateur Visual Studio. L’objectif de cette clé est d’encoder l’intention de l’utilisateur Visual Studio. Pour configurer l’ordinateur client de façon à bloquer les mises à jour de l’administrateur, affectez la valeur 1 à la clé **AdministratorUpdatesOptOut**   REG_DWORD. **** L’absence de clé ou une valeur définie égale à **0** signifie que l’utilisateur Visual Studio souhaite recevoir des mises à jour de l’administrateur pour Visual Studio.

    Notez que la ****   clé AdministratorUpdatesOptOut (pour l’encodage de l’intention du développeur) est hiérarchisée par rapport à la clé **AdministratorUpdatesEnabled**   , qui encode l’intention de l’administrateur informatique. Si **AdministratorUpdatesOptOut**   a la valeur **1**, la mise à jour est bloquée sur le client, même si la clé **AdministratorUpdatesEnabled**   est également définie sur **1**.Cette action suppose que les administrateurs informatiques peuvent accéder et surveiller les développeurs qui choisissent de se désabonner, et que les deux parties peuvent ensuite discuter des besoins les plus importants.Les administrateurs informatiques peuvent toujours modifier l’une ou l’autre clé chaque fois qu’ils le souhaitent.
 
* **Emplacement des bits du produit mis à jour**: la plupart du temps, les ordinateurs clients téléchargent les bits du produit mis à jour à partir d’Internet via le CDN Microsoft. Ce scénario requiert que les ordinateurs clients aient accès à Internet. Certaines entreprises, toutefois, limitent les ordinateurs clients pour installer et mettre à jour uniquement les bits à partir d’un emplacement de disposition réseau interne. Pour vous assurer que les mises à jour de l’administrateur peuvent être appliquées à partir d’un emplacement réseau interne, les conditions suivantes doivent être remplies : 

  - L’ordinateur client doit avoir installé à l’origine le produit à partir d’un emplacement de disposition réseau (c’est-à-dire un cache d’installation local). 
  - Cet emplacement de disposition réseau (où le client installé à l’origine) a été [mis à jour pour contenir les bits du produit mis à jour](../install/update-a-network-installation-of-visual-studio.md) spécifiés par la mise à jour de l’administrateur. 
 
* **Forcer la mise à jour, même si Visual Studio est en cours d’utilisation**: Visual Studio doit être fermé avant l’installation de la mise à jour. Si Visual Studio est ouvert ou en cours d’utilisation, l’installation de la mise à jour sera abandonnée. Un moyen simple de s’assurer que Visual Studio est fermé consiste à configurer le gestionnaire de confirmation pour qu’il applique la mise à jour juste après le redémarrage de l’ordinateur. Vous pouvez également utiliser le `--force` paramètre pour forcer l’arrêt de Visual Studio. Le fait de forcer la fermeture de Visual Studio peut entraîner une perte de travail. Utilisez-le avec précaution. L’exécution d’une mise à jour d’administrateur dans le contexte système par défaut ignorera l' `–-force` indicateur. vous devrez donc configurer la mise à jour de l’administrateur pour qu’elle soit exécutée dans le contexte de l’utilisateur.
 
* **Adhérence** de la ligne de base de maintenance : comme décrit ci-dessus, les mises à jour d’administrateur qui sont des mises à jour de fonctionnalités font progresser une installation de Visual Studio vers une version mineure plus récente du produit. Toutefois, les équipes de développement doivent parfois conserver un niveau de ligne de base de maintenance stable et sécurisé particulier, et elles souhaitent contrôler le moment où leurs clients avancent vers une version mineure plus récente. Pour configurer un ordinateur client de façon à ce qu’il reste sur une ligne de base de maintenance et ignorer les mises à jour de fonctionnalités d’administrateur indésirables qui lui sont envoyées, vous devez créer et définir la valeur de données **BaselineStickinessVersions2019** REG_SZ sur une chaîne qui représente les lignes de base autorisées que l’ordinateur client peut aligner et rester.  La chaîne peut contenir une séquence de versions de ligne de base de maintenance, séparées par des virgules, telles que **16.4.0, 16.7.0**. N’importe quel nombre de versions de ligne de base de maintenance peuvent être incluses dans la chaîne, et le mot **tout**, qui est un raccourci pour référencer toutes les lignes de base de maintenance prises en charge, est également pris en charge. 

     Si la `BaselineStickinessVersions2019` valeur de Registre est incorrecte, l’installation de toutes les mises à jour de fonctionnalités sera bloquée sur l’ordinateur. Veuillez également prêter attention aux [délais pris en charge pour les mises à jour des fonctionnalités Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs). Bien qu’il soit techniquement possible d’appliquer des mises à jour de fonctionnalités qui ont atteint la fin de leur durée de vie, nous ne le recommandons pas, car ils ne seront plus pris en charge et, par conséquent, potentiellement non sécurisés.

### <a name="methods-for-configuring-an-administrator-update"></a>Méthodes de configuration d’une mise à jour d’administrateur

Il existe trois méthodes principales de configuration des mises à jour de l’administrateur : une clé de Registre, un fichier de configuration sur l’ordinateur client ou une modification du package de déploiement Configuration Manager lui-même.   

* **Clé de Registre**: les mises à jour de l’administrateur recherchent des clés de Registre spécifiques dans l’un des emplacements Visual Studio standard, comme décrit dans la documentation [définir les valeurs par défaut pour les déploiements d’entreprise]. Les options contrôlées par les clés de Registre sont des éléments tels que **AdministratorUpdatesOptOut** REG_DWORD, **AdministratorUpdatesOptOut**   REG_DWORD et **BaselineStickinessVersions2019** REG_SZ. L’accès administrateur sur l’ordinateur client est requis pour créer et définir la valeur des clés de registre. 
 
* **Fichier de configuration**: certains paramètres peuvent être conservés sur l’ordinateur client dans un fichier de configuration facultatif, ce qui vous permet de les configurer une seule fois et de les appliquer à toutes les futures mises à jour de l’administrateur. L’approche du fichier de configuration se comporte comme une clé de Registre et est une machine à l’ensemble de l’ordinateur, ce qui signifie qu’elle s’appliquera à toutes les installations de Visual Studio installées sur l’ordinateur client. L’emplacement standard du fichier de configuration est `C:\ProgramData\Microsoft\VisualStudio\updates.config` . Toutefois, si vous souhaitez utiliser un autre emplacement pour stocker le fichier, vous pouvez le faire en créant une clé de Registre Reg_SZ appelée **UpdateConfigurationFile** et en définissant la valeur de cette clé sur le chemin d’accès de votre fichier de configuration. Cette clé de Registre peut être placée dans l’un des emplacements de registre de Visual Studio, comme décrit dans [définir les valeurs par défaut pour les déploiements d’entreprise](../install/set-defaults-for-enterprise-deployments.md). Si vous choisissez d’ajouter une valeur de Registre pour un emplacement de fichier de configuration personnalisé, il recherchera ce fichier ; Si le fichier n’existe pas, une exception est levée et la mise à jour échoue.    
 
Le fichier de configuration, au format JSON, prend en charge l’option `installerUpdateArgs` qui est un tableau de chaînes séparées par des virgules qui spécifient d’autres commutateurs que vous pouvez passer dans le programme d’installation de Visual Studio. Si le contenu du fichier contient un champ non valide ou une option qui n’est pas prise en charge, la mise à jour échoue. Pour plus d’informations, consultez [utiliser des paramètres de ligne de commande pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).
 
Voici un exemple de fichier de configuration : 

```
“installerUpdateArgs” : [“--quiet”, “--noWeb”], 

“checkPendingReboot” :  “true” 
```

* **Mise à jour manuelle du package de mises à jour de l’administrateur dans SCCM**: les paramètres de ligne de commande d’un package de mise à jour d’administrateur individuel dans SCCM peuvent également être modifiés manuellement.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>Vérification, rapports et dépannage des codes d’erreur

### <a name="determining-that-visual-studio-was-updated"></a>Détermination de la mise à jour de Visual Studio

Vous pouvez utiliser l’une des méthodes suivantes pour vérifier que la mise à jour de l’administrateur a été correctement installée : 

* Sur l’ordinateur client, démarrez Visual Studio 2019, sélectionnez **aide**   >  **à propos** de, puis vérifiez que le numéro de version correspond au dernier numéro du titre de la mise à jour prévue. 

* Utilisez l’outil **vswhere** sur l’ordinateur client pour identifier les différentes versions de Visual Studio sur l’ordinateur. Pour plus d’informations, consultez [outils pour la détection et la gestion des instances de Visual Studio](../install/tools-for-managing-visual-studio-instances.md). 

* Chaque tentative de mise à jour administrative génère plusieurs fichiers journaux dans le répertoire de l’ordinateur client `%temp%` qui capturent la progression de l’opération de mise à jour.Triez le dossier par date et recherchez les fichiers qui commencent  `dd_updatedriver` ,  `dd_bootstrapper` ,  `dd_client` et  `dd_setup`   pour les mises à jour administratives, le programme d’amorçage, le Visual Studio installer et le moteur d’installation, respectivement.Vérifiez que ces fichiers journaux contiennent un 0, indiquant que la mise à jour a été appliquée avec succès. Notez que ces fichiers journaux peuvent également être utilisés pour vérifier que le fichier de configuration est en cours d’utilisation. Pour plus d’informations, reportez-vous à l' [outil de collecte de journaux de Visual Studio](https://www.microsoft.com/download/details.aspx?id=12493) .     

### <a name="error-codes-and-conditions"></a>Codes d’erreur et conditions

>[!IMPORTANT]
> N’oubliez pas que Visual Studio doit être fermé avant l’installation de la mise à jour. Si Visual Studio est ouvert ou en cours d’utilisation, l’installation de la mise à jour est annulée.

Les mises à jour administratives peuvent renvoyer les codes de retour suivants :  

| Code d'erreur | Définition |
|--|:-|
| 0 | La mise à jour administrative a été correctement installée. |
| 1001 | Visual Studio Installer ou un processus d’installation associé est en cours d’exécution. La mise à jour n’est pas appliquée. |
| 1002 | Visual Studio Installer est suspendu. La mise à jour n’est pas appliquée. |
| 1003 | Visual Studio est en cours d’exécution. La mise à jour n’est pas appliquée. Cette condition peut être remplacée à l’aide de l' `--force` indicateur. |
| 1004 | Aucun Internet détecté.La mise à jour n’a pas pu contacter l’emplacement Internet contenant les fichiers mis à jour. La mise à jour n’est pas appliquée. |
| 1005 | La  ****   valeur de Registre AdministratorUpdatesEnabled est définie sur **0** ou n’est pas définie du tout. La mise à jour n’est pas appliquée. |
| 1006 | La  ****   valeur de Registre AdministratorUpdatesOptOut est définie sur **1**. La mise à jour n’est pas appliquée. La clé est destinée aux ordinateurs clients qui ne doivent pas être mis à jour par l’administrateur. |
| 1007 | Le Visual Studio Installer n’est pas installé. |
| 1008 | La valeur de Registre **BaselineStickinessVersions2019** n’est pas dans un format lisible. La valeur de registre doit inclure **toutes les** versions ou des versions valides avec le numéro de build défini sur 0 explicitement, par exemple, X. Y. 0. |
| 3010 | Le système nécessite un redémarrage.La mise à jour a peut-être été appliquée ou non. Redémarrez l’ordinateur et réessayez d’effectuer la mise à jour. |
| Autre | Une erreur s’est produite lors de la tentative d’application de la mise à jour.La mise à jour n’est pas appliquée. |

Pour obtenir une liste exhaustive des codes d’erreur du client, consultez [utiliser des paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md). 

## <a name="feedback-and-support"></a>Commentaires et support
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Vous pouvez utiliser les méthodes suivantes pour fournir des commentaires sur les mises à jour de l’Administrateur Visual Studio ou pour signaler des problèmes qui affectent les mises à jour :
* Reportez-vous à la [résolution des problèmes d’installation et de mise à niveau de Visual Studio](../install/troubleshooting-installation-issues.md) .
* Posez des questions à la Communauté lors de la [configuration visuelle Q&un forum](https://docs.microsoft.com/answers/topics/vs-setup.html).
* Accédez à la [page de support de Visual Studio](https://visualstudio.microsoft.com/vs/support/)et vérifiez si votre problème est mentionné dans le Forum aux questions.  Vous pouvez également sélectionner le bouton de [lien support](https://visualstudio.microsoft.com/vs/support/#talktous) pour l’aide de conversation.
* [Fournissez des commentaires sur les fonctionnalités ou signalez un problème](https://aka.ms/vs/wsus/feedback) à l’équipe Visual Studio pour cette expérience.
* Contactez le responsable technique de votre organisation pour Microsoft.

## <a name="see-also"></a>Voir aussi
* [Activation des mises à jour de l’administrateur](../install/enabling-administrator-updates.md)    
* [Guide de l’Administrateur Visual Studio](../install/visual-studio-administrator-guide.md)
* [Cycle de vie et maintenance des produits Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Notes de publication de Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Notes de publication de Visual Studio 2017](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [Installer Visual Studio](../install/install-visual-studio.md)
* [Utilisation des paramètres de ligne de commande pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Outils de détection et de gestion des instances de Visual Studio](../install/tools-for-managing-visual-studio-instances.md)
* [Créer une installation réseau de Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Guide pratique pour définir des paramètres dans un fichier réponse](../install/automated-installation-with-response-file.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](../install/controlling-updates-to-visual-studio-deployments.md)
* [FAQ sur le catalogue Microsoft Update](https://www.catalog.update.microsoft.com/faq.aspx)
* [Documentation de Microsoft Endpoint Configuration Manager (SCCM)](https://docs.microsoft.com/mem/configmgr)
* [Importer des mises à jour à partir de Microsoft Catalog dans Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Documentation Windows Server Update Services (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
