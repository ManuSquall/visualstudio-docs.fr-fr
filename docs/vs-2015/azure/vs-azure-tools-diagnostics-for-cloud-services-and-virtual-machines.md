---
title: Configurer les diagnostics pour Azure Cloud Services et machines virtuelles | Microsoft Docs
description: Découvrez comment configurer les diagnostics pour le débogage des services cloud Azure et machines virtuelles (VM) dans Visual Studio.
author: mikejo5000
manager: douge
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 4448825c5d443887833a405aab14d2243a0e5216
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002085"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Configurer les diagnostics pour Azure Cloud Services et les machines virtuelles Azure
Lorsque vous avez besoin résoudre les problèmes d’un service cloud Azure ou une machine virtuelle, vous pouvez utiliser Visual Studio pour configurer plus facilement les Diagnostics Azure. Les Diagnostics capturent les données système et les données de journalisation sur les machines virtuelles et les instances de machine virtuelle qui exécutent votre service cloud. Les données de diagnostic sont transférées vers un compte de stockage que vous choisissez. Pour plus d’informations sur les diagnostics journalisation dans Azure, consultez [activer la journalisation des diagnostics pour les applications Web dans Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

Dans cet article, nous vous montrons comment utiliser Visual Studio pour activer et configurer les Diagnostics de Azure, à la fois avant et après le déploiement. Découvrez comment configurer les Diagnostics sur des machines virtuelles, comment sélectionner les types d’informations de diagnostic pour collecter et comment afficher les informations après leur collecte.

Vous pouvez utiliser une des options suivantes pour configurer les Diagnostics de Azure :

* Modifier les paramètres de diagnostic dans le **Configuration des Diagnostics** boîte de dialogue dans Visual Studio. Les paramètres sont enregistrés dans un fichier nommé diagnostics.wadcfgx (dans Azure SDK 2.4 et versions antérieures, le fichier est nommé diagnostics.wadcfg). Vous vous pouvez également modifier directement le fichier de configuration. Si vous mettre à jour manuellement le fichier, la modifications de configuration prennent effet la prochaine fois que vous déployez le cloud service vers Azure ou exécuter le service dans l’émulateur.
* Utiliser Cloud Explorer ou l’Explorateur de serveurs dans Visual Studio pour modifier les paramètres de diagnostic pour un service cloud ou d’un ordinateur virtuel qui est en cours d’exécution.

## <a name="azure-sdk-26-diagnostics-changes"></a>Modifications des diagnostics Azure SDK 2.6
Les modifications suivantes s’appliquent à Azure SDK 2.6 et versions ultérieures projets dans Visual Studio :

* L’émulateur local prend désormais en charge les diagnostics. Cela signifie que vous pouvez collecter des données de diagnostic et vous assurer que votre application crée les traces appropriées lorsque vous développez et testez dans Visual Studio. La chaîne de connexion `UseDevelopmentStorage=true` Active la collecte des données de diagnostic pendant l’exécution de votre projet de service cloud dans Visual Studio à l’aide de l’émulateur de stockage Azure. Toutes les données de diagnostic sont collectées dans le compte de stockage stockage de développement.
* La chaîne de connexion de compte de stockage diagnostics `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` est stocké dans le fichier de configuration (.cscfg) du service. Dans Azure SDK 2.5, le compte de stockage de diagnostics est spécifié dans le fichier diagnostics.wadcfgx.

La chaîne de connexion fonctionne différemment à certains égards clés dans Azure SDK 2.6 et ultérieur par rapport à Azure SDK 2.4 et versions antérieures :

* Dans Azure SDK 2.4 et versions antérieures, la chaîne de connexion est utilisée comme un runtime par les diagnostics de plug-in pour obtenir les informations de compte de stockage pour le transfert des journaux de diagnostic.
* Dans Azure SDK 2.6 et versions ultérieures, Visual Studio utilise la chaîne de connexion des diagnostics pour configurer l’Extension de Diagnostics Azure avec les informations de compte de stockage appropriées lors de la publication. Vous pouvez utiliser la chaîne de connexion pour définir les différents comptes de stockage pour différentes configurations de service utilisé par Visual Studio lors de la publication. Toutefois, étant donné que les diagnostics de plug-in n’est pas disponible après Azure SDK 2.5, le fichier .cscfg par lui-même ne peut pas configurer l’extension de diagnostics. Vous devez configurer l’extension séparément à l’aide des outils tels que Visual Studio ou PowerShell.
* Pour simplifier le processus de configuration de l’extension de diagnostics à l’aide de PowerShell, la sortie du package à partir de Visual Studio inclut le fichier XML de configuration publique pour l’extension de diagnostics pour chaque rôle. Visual Studio utilise la chaîne de connexion des diagnostics pour renseigner les informations de compte de stockage dans la configuration publique. Les fichiers de configuration publique sont créés dans le dossier Extensions. Les fichiers de configuration publique utilisent le modèle de nommage PaaSDiagnostics. &lt;nom_rôle\>. PubConfig.xml. Tous les déploiements basés sur PowerShell peuvent utiliser ce modèle pour mapper chaque configuration à un rôle.
* Le [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040) utilise la chaîne de connexion dans le fichier .cscfg pour accéder aux données de diagnostic. Les données apparaissent sur le **surveillance** onglet. La chaîne de connexion est nécessaire pour configurer le service pour afficher les données d’analyse détaillées dans le portail.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Migrer des projets vers Azure SDK 2.6 et versions ultérieures
Lorsque vous migrez à partir d’Azure SDK 2.5 vers Azure SDK 2.6 ou version ultérieure, si vous avez un compte de stockage de diagnostics spécifié dans le fichier .wadcfgx, le compte de stockage reste dans ce fichier. Pour tirer parti de la flexibilité de l’utilisation de comptes de stockage différents pour différentes configurations de stockage, vous devez ajouter manuellement la chaîne de connexion à votre projet. Si vous migrez un projet à partir d’Azure SDK 2.4 ou version antérieure vers Azure SDK 2.6, les chaînes de connexion de diagnostic sont conservées. Toutefois, notez les modifications apportées à la manière dont les chaînes de connexion sont traitées dans Azure SDK 2.6, décrit dans la section précédente.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Comment Visual Studio détermine le compte de stockage de diagnostics
* Si une chaîne de connexion des diagnostics est spécifiée dans le fichier .cscfg, Visual Studio l’utilise pour définir l’extension des diagnostics lors de la publication et lorsqu’il génère les fichiers XML de configuration publique durant l’empaquetage.
* Si une chaîne de connexion de diagnostic n’est pas spécifiée dans le fichier .cscfg, Visual Studio revient à l’aide du compte de stockage qui est spécifié dans le fichier .wadcfgx pour configurer l’extension de diagnostics pour la publication et pour générer le fichier XML de configuration publique fichiers durant l’empaquetage.
* La chaîne de connexion des diagnostics dans le fichier .cscfg est prioritaire sur le compte de stockage dans le fichier .wadcfgx. Si une chaîne de connexion des diagnostics est spécifiée dans le fichier .cscfg, Visual Studio utilise cette chaîne de connexion et ignore le compte de stockage dans .wadcfgx.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>Quelle est la case à cocher « Mettre à jour des chaînes de connexion stockage développement... » ?
Le **mettre à jour les chaînes de connexion de stockage de développement pour les Diagnostics et la mise en cache avec les informations d’identification de compte de stockage Microsoft Azure lors de la publication vers Microsoft Azure** case à cocher est un moyen pratique pour mettre à jour de n’importe quel stockage de développement chaînes de connexion au compte avec le compte de stockage Azure que vous spécifiez lors de la publication.

Par exemple, si vous sélectionnez cette case à cocher et la chaîne de connexion des diagnostics spécifie `UseDevelopmentStorage=true`, lorsque vous publiez le projet sur Azure, Visual Studio met automatiquement à jour la chaîne de connexion de diagnostic avec le compte de stockage que vous avez spécifié dans l’Assistant Publication. Toutefois, si un compte de stockage réel a été spécifié en tant que la chaîne de connexion de diagnostic, ce compte est utilisé à la place.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Différences de fonctionnalités de diagnostics dans Azure SDK 2.4 et antérieur et. Azure SDK 2.5 et versions ultérieures
Si vous mettez à niveau votre projet à partir d’Azure SDK 2.4 et version antérieure vers Azure SDK 2.5 ou version ultérieure, tenez compte des différences de fonctionnalités de diagnostics suivantes :

* **API de configuration est déconseillées**. Configuration par programmation des diagnostics est disponible dans Azure SDK 2.4 et versions antérieures, mais déconseillée dans Azure SDK 2.5 et versions ultérieures. Si votre configuration des diagnostics est actuellement définie dans le code, vous devez reconfigurer ces paramètres à partir de zéro dans le projet migré pour les diagnostics pour continuer à travailler. Le fichier de configuration de diagnostics pour Azure SDK 2.4 est diagnostics.wadcfg. Le fichier de configuration de diagnostics pour Azure SDK 2.5 et versions ultérieures est diagnostics.wadcfgx.
* **Diagnostics pour les applications de service cloud peut être configuré uniquement au niveau du rôle**. Dans Azure SDK 2.5 et versions ultérieures, vous ne pouvez pas configurer les diagnostics pour les applications de service cloud au niveau de l’instance.
* **Chaque fois que vous déployez votre application, la configuration des diagnostics est mise à jour**. Cela peut entraîner des problèmes de parité si vous modifiez votre configuration des diagnostics à partir de l’Explorateur de serveurs Visual Studio, puis redéployez votre application.
* **Dans Azure SDK 2.5 et versions ultérieures, les vidages sur incident sont configurés dans le fichier de configuration de diagnostics et pas dans le code**. Si vous avez des vidages sur incident configurés dans le code, vous devez transférer manuellement la configuration à partir du code au fichier de configuration. Vidages sur incident ne sont pas transférés lors de la migration vers Azure SDK 2.6.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Activer les diagnostics dans les projets de service cloud avant de les déployer
Dans Visual Studio, vous pouvez collecter des données de diagnostic pour les rôles qui s’exécutent dans Azure lorsque vous exécutez le service dans l’émulateur avant le déploiement. Toutes les modifications apportées aux paramètres de diagnostic dans Visual Studio sont enregistrées dans le fichier de configuration diagnostics.wadcfgx. Ces paramètres spécifient le compte de stockage dans lequel les données de diagnostic sont enregistrées lorsque vous déployez votre service cloud.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Pour activer les diagnostics dans Visual Studio avant le déploiement

1. Dans le menu contextuel pour le rôle, sélectionnez **propriétés**. Dans le rôle **propriétés** boîte de dialogue, sélectionnez le **Configuration** onglet.
2. Dans le **Diagnostics** section, assurez-vous que le **activer les Diagnostics** case à cocher est activée.
   
    ![Accéder à l’option Activer les Diagnostics](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Pour spécifier le compte de stockage pour les données de diagnostic, sélectionnez le bouton de sélection (...).
   
    ![Spécifiez le compte de stockage à utiliser](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. Dans le **créer une chaîne de connexion stockage** boîte de dialogue, spécifiez si vous souhaitez vous connecter à l’aide de l’émulateur de stockage Azure, un abonnement Azure, ou manuellement les informations d’identification entrées.
   
    ![Boîte de dialogue compte de stockage](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)
   
   * Si vous sélectionnez **émulateur Microsoft Azure storage**, la chaîne de connexion a la valeur `UseDevelopmentStorage=true`.
   * Si vous sélectionnez **votre abonnement**, vous pouvez sélectionner l’abonnement Azure que vous souhaitez utiliser et entrez un nom de compte. Pour gérer vos abonnements Azure, sélectionnez **gérer les comptes**.
   * Si vous sélectionnez **manuellement les informations d’identification entrées**, entrez le nom et la clé du compte Azure que vous souhaitez utiliser.
5. Pour afficher le **configuration des Diagnostics** boîte de dialogue, sélectionnez **configurer**. À l’exception de **général** et **répertoires de journaux**, chaque onglet représente une source de données de diagnostic que vous pouvez collecter. La valeur par défaut **général** onglet offre les tests de diagnostic suivantes les options de collecte de données : **uniquement les erreurs**, **toutes les informations**, et **plan personnalisé**. La valeur par défaut **uniquement les erreurs** option utilise le moins de stockage, car elle ne transfère pas les avertissements ou messages de suivi. Le **toutes les informations** option transfère le plus d’informations, utilise le plus de stockage et est par conséquent, l’option la plus coûteuse.

   > [!NOTE]
   > Taille de prise en charge minimale pour « Quota de disque en Mo » est de 4 Go. Toutefois, si vous collectez les vidages de mémoire, augmentez cette à une valeur supérieure à 10 Go.
   >
  
    ![Activer la configuration et les diagnostics Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. Pour cet exemple, sélectionnez le **plan personnalisé** option, vous pouvez personnaliser les données collectées.
7. Dans le **Quota de disque en Mo** boîte, vous pouvez définir la quantité d’espace à allouer dans votre compte de stockage pour les données de diagnostic. Vous pouvez modifier ou acceptez la valeur par défaut.
8. Sous chaque onglet des données de diagnostic que vous souhaitez collecter, activez la **activer le transfert de \<type de journal\>**  case à cocher. Par exemple, si vous souhaitez collecter les journaux d’application, sur le **journaux d’Application** onglet, sélectionnez le **activer le transfert des journaux d’Application** case à cocher. En outre, spécifiez les informations requises par chaque type de données de diagnostic. Pour plus d’informations de configuration pour chaque onglet, consultez la section **configurer des sources de données de diagnostic** plus loin dans cet article. 
9. Après avoir activé la collecte de toutes les données de diagnostic souhaitées, sélectionnez **OK**.
10. Exécutez votre projet de service cloud Azure dans Visual Studio comme d’habitude. Lorsque vous utilisez votre application, les informations du journal que vous avez activé sont enregistrées dans le compte de stockage Azure que vous avez spécifié.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Activer les diagnostics sur des machines virtuelles
Dans Visual Studio, vous pouvez collecter des données de diagnostic pour les machines virtuelles.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Pour activer les diagnostics sur des machines virtuelles

1. Dans l’Explorateur de serveurs, sélectionnez le nœud Azure et vous connecter à votre abonnement Azure, si vous n’êtes pas déjà connecté.
2. Développez le **Machines virtuelles** nœud. Vous pouvez créer une machine virtuelle, ou sélectionnez un nœud existant.
3. Dans le menu contextuel pour la machine virtuelle que vous le souhaitez, sélectionnez **configurer**. La boîte de dialogue de configuration de machine virtuelle s’affiche.
   
    ![Configurer une machine virtuelle Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. S’il n’est pas déjà installé, ajoutez l’extension Microsoft Monitoring Agent Diagnostics. Avec cette extension, vous pouvez collecter des données de diagnostic pour la machine virtuelle Azure. Sous **Extensions installées**, dans le **sélectionner une extension disponible** zone de liste déroulante, sélectionnez **Microsoft Monitoring Agent Diagnostics**.
   
    ![Installer une extension de machine virtuelle Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)
   
    > [!NOTE]
   > Autres extensions de diagnostic sont disponibles pour vos machines virtuelles. Pour plus d’informations, consultez [extensions de machine virtuelle et de fonctionnalités pour Windows](https://docs.microsoft.com/azure/virtual-machines/windows/extensions-features).
   > 
   > 
5. Pour ajouter l’extension et afficher son **configuration des Diagnostics** boîte de dialogue, sélectionnez **ajouter**.
6. Pour spécifier un compte de stockage, sélectionnez **configurer**, puis sélectionnez **OK**.
   
    Chaque onglet (à l’exception de **général** et **répertoires de journaux**) représente une source de données de diagnostic que vous pouvez collecter.
   
    ![Activer la configuration et les diagnostics Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
   
    L’onglet par défaut, **général**, vous offre les options de collection de données de diagnostic suivantes : **uniquement les erreurs**, **toutes les informations**, et **plan personnalisé**. L’option par défaut, **uniquement les erreurs**, prend moins de stockage, car elle ne transfère pas les avertissements ou messages de suivi. Le **toutes les informations** option transfère le plus d’informations et est, par conséquent, l’option la plus coûteuse en termes de stockage.
7. Pour cet exemple, sélectionnez le **plan personnalisé** option afin que vous pouvez personnaliser les données collectées.
8. Le **Quota de disque en Mo** zone spécifie la quantité d’espace vous souhaitez allouer dans votre compte de stockage pour les données de diagnostic. Vous pouvez modifier la valeur par défaut si vous le souhaitez.
9. Sous chaque onglet des données de diagnostic à collecter, sélectionnez son **activer le transfert de \<type de journal\>**  case à cocher.
   
    Par exemple, si vous souhaitez collecter les journaux des applications, sélectionnez le **activer le transfert des journaux d’Application** case à cocher sur la **journaux d’Application** onglet. En outre, spécifiez les informations requises pour chaque type de données de diagnostic. Pour plus d’informations de configuration pour chaque onglet, consultez la section **configurer des sources de données de diagnostic** plus loin dans cet article.
10. Une fois que vous avez activé la collecte de toutes les données de diagnostic que vous souhaitez, sélectionnez **OK**.
11. Enregistrez le projet mis à jour.
    
    Un message dans le **journal des activités Microsoft Azure** fenêtre indique que la machine virtuelle a été mis à jour.

## <a name="set-up-diagnostics-data-sources"></a>Configurer des sources de données de diagnostic
Après avoir activé la collecte des données de diagnostic, vous pouvez choisir exactement quelles sources de données que vous souhaitez collecter, et les informations collectées. Les sections suivantes décrivent les onglets de la **configuration des Diagnostics** boîte de dialogue et indique la signification chaque option de configuration.

### <a name="application-logs"></a>Journaux d’application
Journaux d’application contiennent des informations de diagnostic sont générées par une application web. Si vous souhaitez capturer les journaux des applications, sélectionnez le **activer le transfert des journaux d’Application** case à cocher. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux d’application vers votre compte de stockage, vous devez modifier le **période de transfert (min)** valeur. Vous pouvez également modifier la quantité d’informations consignées dans le journal en définissant le **niveau de journal** valeur. Par exemple, sélectionnez **Verbose** pour obtenir plus d’informations, ou sélectionnez **critique** pour capturer uniquement les erreurs critiques. Si vous avez un fournisseur de diagnostics spécifique qui génère des journaux d’application, vous pouvez capturer les journaux en ajoutant le GUID du fournisseur dans le **GUID du fournisseur** boîte.

  ![Journaux d’application](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Pour plus d’informations sur les journaux d’application, consultez [activer la journalisation des diagnostics pour les applications Web dans Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Journaux d’événements Windows
Pour capturer les journaux des événements Windows, sélectionnez le **activer le transfert des journaux des événements Windows** case à cocher. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux des événements à votre compte de stockage, vous devez modifier le **période de transfert (min)** valeur. Sélectionnez les cases à cocher pour les types d’événements que vous souhaitez suivre.

![Journaux des événements](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Si vous utilisez Azure SDK 2.6 ou version ultérieur et que vous souhaitez spécifier une source de données personnalisée, entrez-la dans le **\<nom de source de données\>** zone de texte, puis **ajouter**. La source de données est ajoutée au fichier diagnostics.cfcfg.

Si vous utilisez Azure SDK 2.5 et que vous souhaitez spécifier une source de données personnalisée, vous pouvez l’ajouter à la `WindowsEventLog` fichier de section de diagnostics.wadcfgx, comme dans l’exemple suivant :

```
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```
### <a name="performance-counters"></a>Compteurs de performance
Informations sur les compteurs de performances peuvent vous aider à localiser les goulots d’étranglement système et affiner les performances des applications et du système. Pour plus d’informations, consultez [créer et utiliser des compteurs de performances dans une application Azure](https://msdn.microsoft.com/library/azure/hh411542.aspx). Pour capturer les compteurs de performances, cochez la **activer le transfert des compteurs de performances** case à cocher. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux des événements à votre compte de stockage, vous devez modifier le **période de transfert (min)** valeur. Sélectionnez les cases à cocher pour les compteurs de performances que vous souhaitez suivre.

![Compteurs de performance](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Pour suivre un compteur de performance qui n’est pas répertorié, entrez le compteur de performances à l’aide de la syntaxe suggérée. puis sélectionnez **ajouter**. Le système d’exploitation sur la machine virtuelle détermine quels compteurs de performance que vous pouvez suivre. Pour plus d’informations sur la syntaxe, consultez [spécifier un chemin d’accès du compteur](https://msdn.microsoft.com/library/windows/desktop/aa373193.aspx).

### <a name="infrastructure-logs"></a>Journaux d’infrastructure
Journaux d’infrastructure contiennent des informations sur l’infrastructure de diagnostic Azure, le module RemoteAccess et remoteforwarder. Pour collecter des informations sur les journaux d’infrastructure, cochez la **activer le transfert des journaux d’Infrastructure** case à cocher. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux d’infrastructure à votre compte de stockage, vous devez modifier le **période de transfert (min)** valeur.

![Journaux d’infrastructure de Diagnostics](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Pour plus d’informations, consultez [collecter des données de journalisation à l’aide d’Azure Diagnostics](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="log-directories"></a>Répertoires de journaux
Répertoires de journaux contiennent des données collectées à partir de répertoires de journaux pour des demandes, les demandes ayant échoué ou les dossiers que vous choisissez Internet Information Services (IIS). Pour capturer des répertoires de journaux, sélectionnez le **activer le transfert des répertoires de journaux** case à cocher. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux à votre compte de stockage, vous devez modifier le **période de transfert (min)** valeur.

Sélectionnez les cases à cocher des journaux que vous souhaitez collecter, par exemple **journaux IIS** et **demandes ayant échoué** journaux. Noms de conteneur de stockage par défaut sont fournis, mais vous pouvez modifier les noms.

Vous pouvez capturer des journaux à partir de n’importe quel dossier. Spécifiez le chemin d’accès dans le **journal du répertoire absolu** section, puis sélectionnez **ajouter un répertoire**. Les journaux sont capturées dans les conteneurs spécifiés.

![Répertoires de journaux](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>Journaux de suivi des événements ETW
Si vous utilisez [suivi d’événements pour Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) et souhaitez capturer les journaux ETW, sélectionnez le **activer le transfert des journaux ETW** case à cocher. Pour augmenter ou diminuer l’intervalle entre les transferts des journaux à votre compte de stockage, vous devez modifier le **période de transfert (min)** valeur.

Les événements sont capturés à partir de sources d’événements et des manifestes d’événements que vous spécifiez. Pour spécifier une source d’événement, dans le **Sources d’événements** section, entrez un nom et sélectionnez **Source d’événement ajouter**. De même, vous pouvez spécifier un manifeste d’événements dans le **manifestes d’événements** section, puis sélectionnez **ajouter un manifeste d’événements**.

![Journaux de suivi des événements ETW](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

L’infrastructure ETW est prise en charge dans ASP.NET via des classes dans le [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) espace de noms. L’espace de noms Microsoft.WindowsAzure.Diagnostics, qui hérite et étend standard [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) classes, permet l’utilisation de [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) une journalisation infrastructure dans l’environnement Azure. Pour plus d’informations, consultez [prendre le contrôle de la journalisation et le suivi dans Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) et [activer les diagnostics dans Azure Cloud Services et machines virtuelles](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Vidages sur incident
Pour capturer des informations sur quand une instance de rôle se bloque, cochez la **activer le transfert des vidages sur incident** case à cocher. (Étant donné qu’ASP.NET gère la plupart des exceptions, il est généralement utile uniquement pour les rôles de travail). Pour augmenter ou diminuer le pourcentage d’espace de stockage dédié aux vidages sur incident, vous devez modifier le **Quota de répertoire (%)** valeur. Vous pouvez modifier le conteneur de stockage où sont stockés les vidages sur incident et indiquez si vous voulez capturer un **complète** ou **Mini** dump.

Les processus actuellement suivis sont répertoriés dans la capture d’écran suivante. Sélectionnez les cases à cocher correspondant aux processus que vous souhaitez capturer. Pour ajouter un autre processus à la liste, entrez le nom du processus, puis sélectionnez **ajouter un processus**.

![Vidages sur incident](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Pour plus d’informations, consultez [prendre le contrôle de la journalisation et le suivi dans Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) et [Microsoft Azure Diagnostics Part 4 : composants de journalisation personnalisés et d’Azure Diagnostics 1.3 changes](http://justazure.com/microsoft-azure-diagnostics-part-4-custom-logging-components-azure-diagnostics-1-3-changes/).

## <a name="view-the-diagnostics-data"></a>Afficher les données de diagnostic
Une fois que vous avez collecté les données de diagnostic pour un service cloud ou d’une machine virtuelle, vous pouvez l’afficher.

### <a name="to-view-cloud-service-diagnostics-data"></a>Pour afficher les données de diagnostic de service cloud
1. Déployez votre service cloud comme d’habitude et puis exécutez la commande.
2. Vous pouvez afficher les données de diagnostic dans un rapport généré par Visual Studio ou dans les tables dans votre compte de stockage. Pour afficher les données dans un rapport, ouvrez Cloud Explorer ou l’Explorateur de serveurs, ouvrez le menu contextuel du nœud pour le rôle que vous souhaitez, puis sélectionnez **afficher les données de Diagnostic**.
   
    ![Afficher les données de diagnostic](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)
   
    Un rapport qui affiche les données disponibles s’affiche.
   
    ![Rapport de Diagnostics Microsoft Azure dans Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)
   
    Si les données les plus récentes n’apparaissent pas, vous devrez peut-être attendre la période de transfert.
   
    Pour mettre immédiatement à jour les données, sélectionnez le **Actualiser** lien. Pour que les données mises à jour automatiquement, sélectionnez un intervalle dans le **actualisation automatique** zone de liste déroulante. Pour exporter les données d’erreur, sélectionnez le **exporter au format CSV** bouton pour créer un fichier de valeurs séparées par des virgules que vous pouvez ouvrir dans une feuille de calcul Excel.
   
    Dans Cloud Explorer ou l’Explorateur de serveurs, ouvrez le compte de stockage qui est associé au déploiement.
3. Ouvrez les tables de diagnostics dans la visionneuse de table, puis passez en revue les données que vous avez collectées. Pour les journaux IIS et les journaux personnalisés, vous pouvez ouvrir un conteneur d’objets blob. Le tableau suivant répertorie les tables ou les conteneurs d’objets blob qui contiennent les données pour les différents fichiers journaux. En plus des données pour ce fichier journal, les entrées de table contiennent **EventTickCount**, **DeploymentId**, **rôle**, et **RoleInstance** , pour vous aider à identifier la machine virtuelle et le rôle généré les données et à quel moment. 
   
   | Données de diagnostic | Description | Emplacement |
   | --- | --- | --- |
   | Journaux d’application |Les journaux générés par votre code en appelant des méthodes de la **System.Diagnostics.Trace** classe. |WADLogsTable |
   | Journaux des événements |Données dans les journaux des événements Windows sur les machines virtuelles. Windows stocke les informations dans ces journaux, mais les applications et services utilisent également les journaux pour signaler des erreurs ou enregistrent des informations. |WADWindowsEventLogsTable |
   | Compteurs de performance |Vous pouvez collecter des données sur n’importe quel compteur de performance qui est disponible sur la machine virtuelle. Le système d’exploitation fournit des compteurs de performances qui comprennent de nombreuses statistiques, tels que le temps processeur et de l’utilisation de mémoire. |WADPerformanceCountersTable |
   | Journaux d’infrastructure |Journaux sont générés à partir de l’infrastructure de diagnostics elle-même. |WADDiagnosticInfrastructureLogsTable |
   | Journaux IIS |Journaux qui enregistrent les requêtes web. Si votre service cloud Obtient une quantité importante de trafic, ces journaux peuvent être longs. Il est judicieux de collecter et stocker ces données uniquement lorsque vous en avez besoin. |Vous pouvez consulter les journaux de demandes ayant échoué dans le conteneur d’objets blob sous wad-iis-failedreqlogs, sous un chemin d’accès pour ce déploiement, le rôle et l’instance. Vous pouvez trouver les journaux complets sous wad-iis-logfiles. Les entrées pour chaque fichier sont effectuées dans la table WADDirectories. |
   | Vidages sur incident |Fournit des images binaires du processus de votre service cloud (généralement un rôle de travail). |conteneur d’objets blob WAD-crush-dumps |
   | Fichiers journaux personnalisés |Journaux de données que vous avez prédéfinis. |Vous pouvez spécifier dans le code de l’emplacement des fichiers journaux personnalisés dans votre compte de stockage. Par exemple, vous pouvez spécifier un conteneur d’objets blob personnalisé. |
4. Si les données de n’importe quel type sont tronquées, vous pouvez essayer d’augmenter la mémoire tampon de données de type ou de réduire l’intervalle entre les transferts de données à partir de la machine virtuelle à votre compte de stockage.
5. (Facultatif) Purger les données du compte de stockage occasionnellement afin de réduire les coûts de stockage.
6. Lorsque vous effectuez un déploiement complet, le fichier diagnostics.cscfg (.wadcfgx pour Azure SDK 2.5) est mis à jour dans Azure et votre service cloud sélectionne toutes les modifications à votre configuration de diagnostics. Si au lieu de cela, vous mettez à jour un déploiement existant, le fichier .cscfg n’est pas mis à jour dans Azure. Vous pouvez toujours modifier les paramètres de diagnostic, cependant, en suivant les étapes décrites dans la section suivante. Pour plus d’informations sur l’exécution d’un déploiement complet et la mise à jour un déploiement existant, consultez [Assistant Publication d’Application Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Pour afficher les données de diagnostics de machine virtuelle
1. Dans le menu contextuel pour la machine virtuelle, sélectionnez **afficher les données de Diagnostics**.
   
    ![Afficher les données de diagnostic dans une machine virtuelle Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)
   
    Le **résumé des Diagnostics** boîte de dialogue s’affiche.
   
    ![Résumé des diagnostics de machine virtuelle Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)  
   
    Si les données les plus récentes n’apparaissent pas, vous devrez peut-être attendre la période de transfert.
   
    Pour mettre immédiatement à jour les données, sélectionnez le **Actualiser** lien. Pour que les données mises à jour automatiquement, sélectionnez un intervalle dans le **actualisation automatique** zone de liste déroulante. Pour exporter les données d’erreur, sélectionnez le **exporter au format CSV** bouton pour créer un fichier de valeurs séparées par des virgules que vous pouvez ouvrir dans une feuille de calcul Excel.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Configurer les diagnostics de service cloud après le déploiement
Si vous recherchez des informations sur un problème avec un service cloud qui est déjà en cours d’exécution, vous pouvez souhaiter collecter des données que vous n’avez pas spécifié avant le déploiement initial du rôle. Dans ce cas, vous pouvez commencer à collecter ces données en modifiant les paramètres dans l’Explorateur de serveurs. Vous pouvez configurer les diagnostics pour une instance unique ou pour toutes les instances d’un rôle, selon que vous ouvrez le **Configuration des Diagnostics** boîte de dialogue dans le menu contextuel pour l’instance ou du rôle. Si vous configurez le nœud de rôle, les modifications que vous apportez s’appliquent à toutes les instances. Si vous configurez le nœud d’instance, les modifications que vous apportez s’appliquent uniquement à cette instance.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Pour configurer les diagnostics pour un service cloud en cours d’exécution
1. Dans l’Explorateur de serveurs, développez le **Services Cloud** nœud, puis développez la liste des nœuds pour trouver le rôle ou instance (ou les deux) que vous souhaitez examiner.
   
    ![Configurer les diagnostics](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. Dans le menu contextuel pour un nœud d’instance ou rôle, sélectionnez **mise à jour les paramètres de diagnostic**, puis sélectionnez les paramètres de diagnostic que vous souhaitez collecter.
   
    Pour plus d’informations sur les paramètres de configuration, consultez la section **configurer des sources de données de diagnostic** dans cet article. Pour plus d’informations sur la façon d’afficher les données de diagnostic, consultez la section **afficher les données de diagnostic** dans cet article.
   
    Si vous modifiez la collecte de données dans l’Explorateur de serveurs, les modifications restent en vigueur jusqu’au redéploiement complet de votre service cloud. Si vous utilisez la valeur par défaut des paramètres de publication, les modifications ne sont pas remplacées. Paramètre de publication de la valeur par défaut est de mettre à jour le déploiement existant, plutôt que d’effectuer un redéploiement complet. Pour vous assurer que les paramètres sont effacés au moment du déploiement, accédez à la **paramètres avancés** onglet dans l’Assistant Publication, puis décochez la **mise à jour de déploiement** case à cocher. Lorsque vous redéployez avec cette case à cocher désactivée, les paramètres reviennent à ceux du fichier .wadcfgx (ou .wadcfg) en tant que jeu par le biais du **propriétés** éditeur pour le rôle. Si vous mettez à jour votre déploiement, Azure conserve les paramètres précédents.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Résoudre les problèmes de service cloud Azure
Si vous rencontrez des problèmes avec vos projets de service cloud, par exemple, un rôle reste bloqué à l’état « occupé », à plusieurs reprises est recyclé, ou lève une erreur serveur interne, il existe outils et techniques que vous pouvez utiliser pour diagnostiquer et corriger le problème. Pour obtenir des exemples spécifiques de problèmes courants et solutions et pour une vue d’ensemble des concepts et des outils que vous pouvez utiliser pour diagnostiquer et corriger ces erreurs, consultez [les données de diagnostic de calcul PaaS Azure](http://blogs.msdn.com/b/kwill/archive/2013/08/09/windows-azure-paas-compute-diagnostics-data.aspx).

## <a name="q--a"></a>Questions et réponses
**Quelle est la taille de mémoire tampon et quelle doit être ?**

Sur chaque instance de machine virtuelle, des quotas limitent la quantité de données de diagnostic peut être stockée sur le système de fichiers local. En outre, vous spécifiez une taille de mémoire tampon pour chaque type de données de diagnostic qui est disponibles. Cette taille de mémoire tampon agit comme un quota individuel pour ce type de données. Pour déterminer le quota global et la quantité de mémoire restante, consultez le bas de la boîte de dialogue pour le type de données de diagnostic. Si vous spécifiez des mémoires tampons plus volumineuses ou des types de données, vous vous approchez le quota global. Vous pouvez modifier le quota global en modifiant le fichier de configuration diagnostics.wadcfg ou .wadcfgx. Les données de diagnostic sont stockées sur le même système de fichiers en tant que données de votre application. Si votre application utilise une grande quantité d’espace disque, vous ne devez pas augmenter le quota de diagnostic global.

**Quelle est la période de transfert et quelle doit être sa durée ?**

La période de transfert est la quantité de temps qui s’écoule entre les données de capture. Après chaque période de transfert, les données sont déplacées du système de fichiers local sur une machine virtuelle aux tables dans votre compte de stockage. Si la quantité de données collectées dépasse le quota avant la fin d’une période de transfert, les données antérieures sont ignorées. Si vous perdez des données, car vos données dépassent la taille de mémoire tampon ou le quota global, vous souhaiterez diminuer la période de transfert.

**Quel fuseau horaire se trouvent les horodatages dans ?**

Horodatages sont dans le fuseau horaire local du centre de données qui héberge votre service cloud. Les suivant trois colonnes d’horodatage dans les tables du journal sont utilisés :

* **PreciseTimeStamp**: horodatage ETW de l’événement. Autrement dit, l’heure de l’événement est enregistré à partir du client.
* **HORODATAGE**: la valeur de **PreciseTimeStamp** est arrondi à la limite de fréquence de chargement. Par exemple, si votre fréquence de téléchargement est de 5 minutes et l’événement heure 00:17:12, TIMESTAMP est 00:15:00.
* **Horodatage**: l’horodatage auquel l’entité a été créée dans la table Azure.

**Comment gérer les coûts lors de la collecte des informations de diagnostic ?**

Les paramètres par défaut (**niveau de journal** définie sur **erreur**, et **période de transfert** définie sur **1 minute**) sont conçus pour réduire les coûts. Vos coûts de calcul augmentent lorsque vous collectez des données de diagnostic plus ou si vous diminuez la période de transfert. Ne pas collecter plus de données que vous avez besoin et n’oubliez pas de désactiver la collecte de données lorsque vous n’en avez plus besoin. Vous pouvez toujours réactiver, même au moment de l’exécution, comme décrit précédemment dans cet article.

**Comment collecter les journaux de demandes ayant échoué à partir d’IIS ?**

Par défaut, IIS ne collecte pas les journaux de demandes ayant échoué. Vous pouvez configurer IIS pour collecter les journaux de demandes ayant échoué en modifiant le fichier web.config pour votre rôle web.

**Je n’obtiens pas les informations de trace des méthodes RoleEntryPoint comme OnStart. Quel est le problème ?**

Les méthodes de **RoleEntryPoint** sont appelés dans le contexte de WAIISHost.exe, non dans IIS. Les informations de configuration dans le fichier web.config qui active le traçage ne s’appliquent. Pour résoudre ce problème, ajoutez un fichier .config à votre projet de rôle web et nommez le fichier pour correspondre à l’assembly de sortie qui contient le **RoleEntryPoint** code. Dans le projet de rôle web par défaut, le nom du fichier .config doit être WAIISHost.exe.config. Ajoutez les lignes suivantes à ce fichier :

```
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

Dans le **propriétés** fenêtre, définissez la **Copy to Output Directory** propriété **toujours copier**.

## <a name="next-steps"></a>Étapes suivantes
Pour en savoir plus sur la journalisation des diagnostics dans Azure, consultez [activer les diagnostics dans Azure Cloud Services et machines virtuelles](/azure/cloud-services/cloud-services-dotnet-diagnostics.md) et [activer la journalisation des diagnostics pour les applications Web dans Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

