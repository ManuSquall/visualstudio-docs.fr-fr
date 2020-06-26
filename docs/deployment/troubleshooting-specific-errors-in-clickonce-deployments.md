---
title: Résolution des erreurs spécifiques dans les déploiements ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66a98a822cd9aac6d93b4964e2e8bdadc98972e5
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381897"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>Dépanner des erreurs spécifiques dans les déploiements ClickOnce
Cet article répertorie les erreurs courantes suivantes qui peuvent se produire lorsque vous déployez une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, et fournit des étapes pour résoudre chaque problème.

## <a name="general-errors"></a>Erreurs générales.

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Lorsque vous essayez de localiser un fichier d’application, rien ne se produit ou le fichier XML est rendu dans Internet Explorer, ou vous recevez une boîte de dialogue Exécuter ou enregistrer sous
 Cette erreur est probablement due au fait que les types de contenu (également appelés types MIME) ne sont pas inscrits correctement sur le serveur ou le client.

 Tout d’abord, assurez-vous que le serveur est configuré pour associer l’extension *. application* au type de contenu « application/x-ms-application ».

 Si le serveur est correctement configuré, vérifiez que le .NET Framework 2,0 est installé sur votre ordinateur. Si le .NET Framework 2,0 est installé et que vous rencontrez toujours ce problème, essayez de désinstaller et de réinstaller le .NET Framework 2,0 pour réinscrire le type de contenu sur le client.

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Le message d’erreur indique «Impossible de récupérer l’application. Les fichiers manquants dans le déploiement» ou « le téléchargement de l’application a été interrompu, vérifiez les erreurs réseau et réessayez plus tard »
 Ce message indique qu’un ou plusieurs fichiers référencés par les [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes ne peuvent pas être téléchargés. Le moyen le plus simple de déboguer cette erreur consiste à essayer de télécharger l’URL indiquant [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qu’elle ne peut pas être téléchargée. Voici quelques causes possibles :

- Si le fichier journal indique « (403) interdit » ou « (404) introuvable », vérifiez que le serveur Web est configuré pour ne pas bloquer le téléchargement de ce fichier. Pour plus d’informations, consultez [Problèmes de configuration de serveur et de client lors de déploiements ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

- Si le fichier *. config* est bloqué par le serveur, consultez la section « erreur de téléchargement lorsque vous essayez d’installer une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application qui a un fichier. config » plus loin dans cet article.

- Déterminez si cette erreur s’est produite parce que l' `deploymentProvider` URL du manifeste de déploiement pointe vers un emplacement différent de l’URL utilisée pour l’activation.

- Assurez-vous que tous les fichiers sont présents sur le serveur. le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Journal doit indiquer quel fichier est introuvable.

- Vérifiez s’il existe des problèmes de connectivité réseau. vous pouvez recevoir ce message si votre ordinateur client a été mis hors connexion pendant le téléchargement.

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Erreur de téléchargement lorsque vous essayez d’installer une application ClickOnce avec un fichier. config
 Par défaut, un Visual Basic application Windows comprend un fichier App.config. Un problème se pose quand un utilisateur tente d’installer à partir d’un serveur Web qui utilise Windows Server 2003, car ce système d’exploitation bloque l’installation des fichiers *. config* pour des raisons de sécurité. Pour permettre l’installation du fichier *. config* , cliquez sur **utiliser l’extension de fichier « . deploy »** dans la boîte de dialogue **options de publication** .

 Vous devez également définir les types de contenu (également appelés types MIME) de manière appropriée pour les fichiers. application,. manifest et. deploy. Pour plus d’informations, consultez la documentation de votre serveur Web.

 Pour plus d’informations, consultez « Windows Server 2003 : types de contenu verrouillés » dans [problèmes de configuration des serveurs et des clients dans les déploiements ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Message d’erreur : « l’application n’est pas correctement mise en forme ; » Le fichier journal contient la « signature XML non valide »
 Veillez à mettre à jour le fichier manifeste et à le signer à nouveau. Republiez votre application à l’aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou utilisez Mage pour signer à nouveau l’application.

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Vous avez mis à jour votre application sur le serveur, mais le client ne télécharge pas la mise à jour
 Ce problème peut être résolu en effectuant l’une des tâches suivantes :

- Examinez l' `deploymentProvider` URL dans le manifeste de déploiement. Assurez-vous que vous mettez à jour les bits dans le même emplacement que celui `deploymentProvider` vers lequel pointe.

- Vérifiez l’intervalle de mise à jour dans le manifeste de déploiement. Si cet intervalle est défini sur un intervalle périodique, par exemple une fois toutes les six heures, ne [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] recherche pas une mise à jour tant que cet intervalle n’est pas écoulé. Vous pouvez modifier le manifeste pour rechercher une mise à jour chaque fois que l’application démarre. La modification de l’intervalle de mise à jour est une option pratique pendant le temps de développement pour vérifier que les mises à jour sont en cours d’installation, mais elle ralentit l’activation de l’application.

- Essayez de redémarrer l’application dans le menu Démarrer. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]a peut-être détecté la mise à jour en arrière-plan, mais vous invite à installer les bits lors de la prochaine activation.

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Pendant la mise à jour, vous recevez une erreur avec l’entrée de journal suivante : « la référence dans le déploiement ne correspond pas à l’identité définie dans le manifeste de l’application ».
 Cette erreur peut se produire si vous avez modifié manuellement les manifestes de déploiement et d’application, et que vous avez fait en sorte que la description de l’identité d’un assembly d’un manifeste soit désynchronisée avec l’autre. L’identité d’un assembly se compose de son nom, sa version, sa culture et son jeton de clé publique. Examinez les descriptions des identités dans vos manifestes et corrigez les éventuelles différences.

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>La première activation à partir du disque local ou du CD-ROM a échoué, mais l’activation suivante du menu Démarrer échoue
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]utilise l’URL du fournisseur de déploiement pour recevoir les mises à jour de l’application. Vérifiez que l’emplacement vers lequel pointe l’URL est correct.

#### <a name="error-cannot-start-the-application"></a>Erreur : « impossible de démarrer l’application »
 Ce message d’erreur indique généralement qu’un problème est survenu lors de l’installation de cette application dans le Windows [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Store. L’application a une erreur ou le magasin est endommagé. Le fichier journal peut vous indiquer où l’erreur s’est produite.

 Vous devez effectuer les opérations suivantes :

- Vérifiez que l’identité du manifeste de déploiement, l’identité du manifeste d’application et l’identité de l’application EXE principale sont toutes uniques.

- Vérifiez que les chemins d’accès de vos fichiers ne sont pas plus longs que 100 caractères. Si votre application contient des chemins d’accès de fichiers trop longs, vous risquez de dépasser les limites du chemin d’accès maximal que vous pouvez stocker. Essayez de raccourcir les chemins d’accès et de réinstaller.

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Les paramètres PrivatePath dans le fichier de configuration d’application ne sont pas honorés
 Pour utiliser PrivatePath (chemins de détection de fusion), l’application doit demander une autorisation de confiance totale. Essayez de modifier le manifeste d’application pour demander un niveau de confiance totale, puis réessayez.

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Lors de la désinstallation, un message s’affiche, indiquant « échec de la désinstallation de l’application »
 Ce message indique généralement que l’application a déjà été supprimée ou que le magasin est endommagé. Une fois que vous avez cliqué sur **OK**, l’entrée **Ajouter/supprimer un programme** est supprimée.

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Pendant l’installation, un message s’affiche indiquant que les dépendances de plateforme ne sont pas installées
 Vous ne disposez pas d’une condition préalable dans le GAC (Global Assembly Cache) dont l’application a besoin pour s’exécuter.

## <a name="publishing-with-visual-studio"></a>Publication avec Visual Studio

#### <a name="publishing-in-visual-studio-fails"></a>Échec de la publication dans Visual Studio
 Assurez-vous que vous avez le droit de publier sur le serveur que vous ciblez. Par exemple, si vous êtes connecté à un ordinateur Terminal Server en tant qu’utilisateur ordinaire, et non en tant qu’administrateur, vous ne disposerez probablement pas des droits nécessaires pour publier sur le serveur Web local.

 Si vous publiez avec une URL, assurez-vous que l’ordinateur de destination a FrontPage Server Extensions activé.

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Message d’erreur : impossible de créer le site Web' \<site> '. Les composants de communication avec FrontPage Server Extensions ne sont pas installés.
 Assurez-vous que le Microsoft Visual Studio web Authoring Component est installé sur l’ordinateur à partir duquel vous effectuez la publication. Pour les utilisateurs Express, ce composant n’est pas installé par défaut. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=102310](https://support.microsoft.com/help/945358).

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Message d’erreur : impossible de trouver le fichier’Microsoft. Windows. Common-Controls, version = 6.0.0.0, culture = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture = \* , type = Win32 '
 Ce message d’erreur s’affiche lorsque vous tentez de publier une application WPF avec les styles visuels activés. Pour résoudre ce problème, consultez [Comment : publier une application WPF avec les styles visuels activés](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).

## <a name="using-mage"></a>Utilisation de mage

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Vous avez essayé de vous connecter avec un certificat dans votre magasin de certificats et une boîte de message vide a été reçue
 Dans la boîte de dialogue **signature** , vous devez :

- Sélectionnez **signer avec un certificat stocké**, puis

- Sélectionnez un certificat dans la liste. le premier certificat n’est pas la sélection par défaut.

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Le fait de cliquer sur le bouton « ne pas signer » provoque une exception
 Ce problème est connu sous le nom de bogue. Tous les [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes doivent être signés. Sélectionnez simplement l’une des options de signature, puis cliquez sur **OK**.

## <a name="additional-errors"></a>Erreurs supplémentaires
 Le tableau suivant présente quelques messages d’erreur courants qu’un utilisateur de l’ordinateur client peut recevoir lorsque l’utilisateur installe une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Chaque message d’erreur est indiqué en regard d’une description de la cause la plus probable de l’erreur.

| Message d’erreur | Description |
| - | - |
| Impossible de démarrer l’application. Contactez l’éditeur de l’application.<br /><br /> Impossible de démarrer l’application. Contactez le fournisseur de l’application pour obtenir de l’aide. | Il s’agit de messages d’erreur génériques qui se produisent lorsque l’application ne peut pas être démarrée, et aucune autre raison spécifique ne peut être trouvée. Souvent, cela signifie que l’application est endommagée, ou que le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] magasin est endommagé. |
| Impossible de continuer. L’application n’est pas mise en forme correctement. Contactez l’éditeur de l’application pour obtenir de l’aide.<br /><br /> Échec de la validation de l’application. Impossible de continuer.<br /><br /> Impossible de récupérer les fichiers de l’application. Fichiers endommagés dans le déploiement. | L’un des fichiers manifestes dans le déploiement est syntaxiquement non valide, ou contient un hachage qui ne peut pas être concilié avec le fichier correspondant. Cette erreur peut également indiquer que le manifeste incorporé à l’intérieur d’un assembly est endommagé. Recréez votre déploiement et recompilez votre application, ou recherchez et corrigez les erreurs manuellement dans vos manifestes. |
| Impossible de récupérer l’application. Erreur d’authentification.<br /><br /> L’installation de l’application a échoué. Impossible de trouver les fichiers d’applications sur le serveur. Contactez l’éditeur de l’application ou votre administrateur pour obtenir de l’aide. | Impossible de télécharger un ou plusieurs fichiers du déploiement, car vous n’êtes pas autorisé à y accéder. Cela peut être dû à une erreur 403 interdite qui est renvoyée par un serveur Web, ce qui peut se produire si l’un des fichiers de votre déploiement se termine par une extension qui fait en sorte que le serveur Web le traite comme un fichier protégé. En outre, un répertoire qui contient un ou plusieurs fichiers de l’application peut nécessiter un nom d’utilisateur et un mot de passe pour pouvoir accéder à. |
| Impossible de télécharger l’application. Des fichiers requis sont manquants dans l’application. Contactez le fournisseur de l’application ou votre administrateur système pour obtenir de l’aide. | Un ou plusieurs des fichiers listés dans le manifeste de l’application sont introuvables sur le serveur. Vérifiez que vous avez téléchargé tous les fichiers dépendants du déploiement, puis réessayez. |
| Échec du téléchargement de l’application. Vérifiez votre connexion réseau ou contactez votre administrateur système ou votre fournisseur de services réseau. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Impossible d’établir une connexion réseau au serveur. Examinez la disponibilité du serveur et l’état de votre réseau. |
| URLDownloadToCacheFile a échoué avec HRESULT' \<number> '. Une erreur s’est produite lors de la tentative de téléchargement de' \<file> '. | Si un utilisateur a défini l’option de sécurité avancée d’Internet Explorer sur l’ordinateur cible du déploiement, et si l’URL de configuration de l’application ClickOnce en cours d’installation est redirigée d’un site non sécurisé vers un site sécurisé (ou vice versa), l’installation échouera car l’avertissement Internet Explorer l’interrompt.<br /><br /> Pour résoudre cette erreur, vous pouvez effectuer l’une des tâches suivantes :<br /><br /> -Désactivez l’option de sécurité.<br />-Assurez-vous que l’URL d’installation n’est pas redirigée de manière à modifier les modes de sécurité.<br />-Supprimez complètement la redirection et pointez sur l’URL d’installation réelle. |
| Une erreur s’est produite lors de l’écriture sur le disque dur. L’espace disponible sur le disque est peut-être insuffisant. Contactez le fournisseur de l’application ou votre administrateur système pour obtenir de l’aide. | Cela peut indiquer que l’espace disque est insuffisant pour le stockage de l’application, mais cela peut également indiquer une erreur d’e/s plus générale lorsque vous essayez d’enregistrer les fichiers de l’application sur le lecteur. |
| Impossible de démarrer l’application. Il n’y a pas assez d’espace disponible sur le disque. | Le disque dur est plein. Libérez de l’espace et réessayez d’exécuter l’application. |
| Un trop grand nombre d’activations déployées tente de se charger en même temps. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]limite le nombre d’applications différentes qui peuvent démarrer en même temps. Cela est principalement destiné à vous protéger contre les tentatives malveillantes d’effectuer des attaques par déni de service contre le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] service local ; les utilisateurs qui essaient de démarrer la même application à plusieurs reprises, à la suite d’une succession rapide, ne finissent qu’avec une seule instance de l’application. |
| Les raccourcis ne peuvent pas être activés sur le réseau. | Les raccourcis vers une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application peuvent uniquement être démarrés sur le disque dur local. Ils ne peuvent pas être démarrés en ouvrant une URL qui pointe vers un fichier de raccourci sur un serveur distant. |
| L’application est trop volumineuse pour être exécutée en ligne en mode de confiance partielle. Contactez le fournisseur de l’application ou votre administrateur système pour obtenir de l’aide. | Une application qui s’exécute en mode de confiance partielle ne peut pas être supérieure à la moitié de la taille du quota d’application en ligne, qui est par défaut de 250 Mo. |

## <a name="see-also"></a>Voir aussi
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Dépanner des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)