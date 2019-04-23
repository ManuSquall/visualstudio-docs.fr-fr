---
title: Dépannage d’erreurs spécifiques dans les déploiements ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: c2d337a1ed97524dc04c8154fe2b074baf0921ca
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042379"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>Dépanner des erreurs spécifiques dans les déploiements ClickOnce
Cet article répertorie les erreurs courantes qui peuvent se produire lorsque vous déployez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application et fournit les étapes pour résoudre chaque problème.

## <a name="general-errors"></a>Erreurs générales

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Lorsque vous tentez de rechercher un fichier d’application, rien ne se produit, XML est rendue dans Internet Explorer, ou vous recevez une boîte de dialogue Exécuter ou enregistrer sous
 Cette erreur est probablement due par les types de contenu (également connu sous les types MIME) n’est pas inscrits correctement sur le serveur ou le client.

 Tout d’abord, assurez-vous que le serveur est configuré pour associer le *.application* extension avec le contenu de type « application/x-ms-application. »

 Si le serveur est configuré correctement, vérifiez que le [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] est installé sur votre ordinateur. Si le [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] est installé, et vous voyez toujours ce problème, essayez de désinstaller et réinstaller le [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] pour réinscrire le type de contenu sur le client.

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Message d’erreur indique « Impossible d’extraire l’application. Les fichiers manquants dans le déploiement » ou « téléchargement de l’Application a été interrompue, recherchez les erreurs de réseau et réessayez plus tard »
 Ce message indique qu’un ou plusieurs fichiers référencés par le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes ne peuvent pas être téléchargées. Le moyen le plus simple de déboguer cette erreur consiste à essayer de télécharger l’URL qui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] affirme ne peut pas télécharger. Voici les causes possibles :

- Si le fichier journal stipule « (403) interdit » ou « (404) introuvable », vérifiez que le serveur Web est configuré afin qu’il ne bloque pas le téléchargement de ce fichier. Pour plus d’informations, consultez [Problèmes de configuration de serveur et de client lors de déploiements ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

- Si le *.config* fichier est bloqué par le serveur, consultez la section « erreur de téléchargement lorsque vous essayez d’installer un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application qui dispose d’un fichier .config » plus loin dans cet article.

- Déterminer si cette erreur s’est produite, car le `deploymentProvider` URL dans le manifeste de déploiement pointe vers un emplacement autre que l’URL utilisée pour l’activation.

- Assurez-vous que tous les fichiers sont présents sur le serveur ; le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] journal doit indiquer le fichier qui est introuvable.

- S’il existe des problèmes de connectivité réseau ; Vous pouvez recevoir ce message si votre ordinateur client s’est déconnecté pendant le téléchargement.

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Erreur de téléchargement lorsque vous essayez d’installer une application ClickOnce qui dispose d’un fichier .config
 Par défaut, une application Windows de Visual Basic inclut un fichier App.config. Il y aura un problème lorsqu’un utilisateur tente d’installer à partir d’un serveur Web qui utilise Windows Server 2003, car ce système d’exploitation bloque l’installation du *.config* fichiers pour des raisons de sécurité. Pour activer la *.config* fichier à installer, cliquez sur **utiliser l’extension de fichier « .deploy »** dans le **Options de publication** boîte de dialogue.

 Vous devez également définir les types de contenu (également connu sous les types MIME) en conséquence pour .application, .manifest et .deploy fichiers. Pour plus d’informations, consultez la documentation de votre serveur Web.

 Pour plus d’informations, consultez « Windows Server 2003 : Verrouillé Types de contenu » [problèmes de configuration de serveur et client dans les déploiements ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Message d’erreur : « Application n’est pas formatée ; ». Fichier journal contient « signature XML non valide »
 Vérifiez que le fichier manifest mis à jour et de nouveau signé. Republiez votre application à l’aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou utilisez Mage pour signer à nouveau l’application.

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Mise à jour de votre application sur le serveur, mais le client ne télécharge pas la mise à jour
 Ce problème peut être résolu en effectuant l’une des tâches suivantes :

- Examiner le `deploymentProvider` URL dans le manifeste de déploiement. Assurez-vous que vous mettez à jour les bits contenus dans le même emplacement que `deploymentProvider` pointe vers.

- Vérifiez l’intervalle de mise à jour dans le manifeste de déploiement. Si cet intervalle est défini à un intervalle périodique, par exemple une fois toutes les six heures, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] n’analyse pas une mise à jour jusqu'à ce que cet intervalle est écoulé. Vous pouvez modifier le manifeste pour rechercher une mise à jour chaque fois que l’application démarre. Modification de l’intervalle de mise à jour est une option pratique au moment du développement pour vérifier les mises à jour sont en cours d’installation, mais elle ralentit l’activation de l’application.

- Essayez de redémarrer l’application dans le menu Démarrer. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a pu détecter la mise à jour en arrière-plan, mais vous invitera à installer les bits lors de la prochaine activation.

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Au cours de la mise à jour, vous recevez une erreur qui a l’entrée de journal suivante : « La référence dans le déploiement ne correspond pas à l’identité définie dans le manifeste d’application »
 Cette erreur peut se produire, car vous avez modifié manuellement les manifestes de déploiement et d’application et avez provoqué la description de l’identité d’un assembly dans un manifeste à devenir désynchronisés avec les autres. L’identité d’un assembly se compose de son nom, la version, culture et jeton de clé publique. Examinez les descriptions d’identité dans vos manifestes et corrigez les éventuelles différences.

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Première activation de disque local ou CD-ROM réussit, mais l’activation suivante à partir du Menu Démarrer ne fonctionne pas
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilise l’URL de fournisseur de déploiement pour recevoir les mises à jour pour l’application. Vérifiez que l’emplacement vers lequel pointe l’URL est correcte.

#### <a name="error-cannot-start-the-application"></a>Erreur : « Impossible de démarrer l’application »
 Ce message d’erreur indique généralement qu’il existe un problème d’installation de cette application dans le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] stocker. L’application comporte une erreur ou le magasin est endommagé. Le fichier journal peut vous dire où l’erreur s’est produite.

 Vous devez procédez comme suit :

- Vérifiez que l’identité du manifeste de déploiement, d’identité du manifeste d’application et l’identité de l’application EXE principale sont toutes uniques.

- Vérifiez que les chemins d’accès ne sont pas plus de 100 caractères. Si votre application contient des chemins d’accès de fichier sont trop longs, vous risquez de dépasser les limitations sur le chemin d’accès maximal, que vous pouvez stocker. Essayez de raccourcir les chemins d’accès et le réinstaller.

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Les paramètres PrivatePath définis dans le fichier de configuration d’application ne sont pas respectés.
 Pour utiliser PrivatePath (chemins d’accès de détection de Fusion), l’application doit demander l’autorisation de confiance totale. Essayez de modifier le manifeste d’application pour demander une confiance totale, puis réessayez.

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Pendant la désinstallation un message s’affiche indiquant « Impossible de désinstaller l’application »
 Ce message indique généralement que l’application a déjà été supprimée ou le magasin est endommagé. Après avoir cliqué sur **OK**, le **Ajout/Suppression de programmes** entrée sera supprimée.

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Pendant l’installation, un message s’affiche indiquant que les dépendances de plateforme ne sont pas installés
 Il manque un composant requis dans le GAC (global assembly cache) dont l’application a besoin pour s’exécuter.

## <a name="publishing-with-visual-studio"></a>Publication avec Visual Studio

#### <a name="publishing-in-visual-studio-fails"></a>Échec de la publication dans Visual Studio
 Assurez-vous d’avoir le droit de publier sur le serveur que vous ciblez. Par exemple, si vous êtes connecté à un ordinateur de serveur terminal server en tant qu’un utilisateur ordinaire, pas en tant qu’administrateur, vous ne disposez probablement pas les droits requis pour publier sur le serveur Web local.

 Si vous publiez avec une URL, vérifiez que l’ordinateur de destination a activé les Extensions serveur FrontPage.

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Message d’erreur : Impossible de créer le site Web '\<site >'. Les composants permettant de communiquer avec les Extensions serveur FrontPage ne sont pas installés.
 Assurez-vous d’avoir le Microsoft Visual Studio Web Authoring composant installé sur l’ordinateur que vous publiez à partir de. Pour les utilisateurs d’Express, ce composant n’est pas installé par défaut. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Message d’erreur : Fichier introuvable ' Microsoft.Windows.Common-contrôles, Version = 6.0.0.0, Culture = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture =\*, Type = win32'
 Ce message d’erreur s’affiche lorsque vous tentez de publier une application WPF avec les styles visuels sont activés. Pour résoudre ce problème, consultez [Comment : Publier une Application WPF avec les Styles visuels activés](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).

## <a name="using-mage"></a>À l’aide de Mage

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Vous avez essayé de vous connecter avec un certificat dans votre magasin de certificats et une boîte de message vide
 Dans le **signature** boîte de dialogue, vous devez :

- Sélectionnez **signer avec un certificat stocké**, et

- Sélectionnez un certificat dans la liste ; le premier certificat n’est pas la sélection par défaut.

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>En cliquant sur le bouton « Se ne » provoque une exception
 Ce problème est un bogue connu. Tous les [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes sont requis pour être signé. Sélectionnez simplement une des options de signature, puis cliquez sur **OK**.

## <a name="additional-errors"></a>Autres erreurs
 Le tableau suivant présente quelques messages d’erreur courants qu’un utilisateur de l’ordinateur client peut recevoir lorsque l’utilisateur installe un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Chaque message d’erreur est répertorié en regard d’une description de la cause la plus probable pour l’erreur.

| Message d'erreur | Description |
| - | - |
| Impossible de démarrer l’application. Contactez l’éditeur de l’application.<br /><br /> Impossible de démarrer l’application. Contactez le fournisseur de l’application. | Il s’agit des messages d’erreur génériques qui se produisent lors de l’application ne peut pas être démarrée, et aucune autre raison spécifique ne peut être trouvé. Fréquemment cela signifie que l’application est endommagée, ou qui le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] magasin est endommagé. |
| Impossible de poursuivre. L’application n’est pas formatée. Contactez l’éditeur de l’application.<br /><br /> Échec de la validation de l’application. Impossible de continuer.<br /><br /> Impossible de récupérer les fichiers d’application. Fichiers endommagés dans le déploiement. | Un des fichiers manifeste de déploiement n’est syntaxiquement pas valide ou contient un hachage qui ne peut pas être réconcilié avec le fichier correspondant. Cette erreur peut également indiquer que le manifeste incorporé à l’intérieur d’un assembly est endommagé. Recréez votre déploiement et recompiler votre application, ou recherchez et résolvez manuellement les erreurs dans vos manifestes. |
| Impossible de récupérer l’application. Erreur d’authentification.<br /><br /> Échec de l’installation de l’application. Impossible de localiser les fichiers des applications sur le serveur. Contactez votre administrateur ou le serveur de publication d’application. | Un ou plusieurs fichiers dans le déploiement ne peut pas être téléchargés, car vous n’êtes pas autorisé à y accéder. Cela peut être dû à une erreur 403 Interdit retourné par un serveur Web, ce qui peut se produire si l’un des fichiers dans votre déploiement se termine par une extension qui rend le serveur Web à traiter comme un fichier protégé. En outre, un répertoire qui contient une ou plusieurs des fichiers de l’application peut nécessiter un nom d’utilisateur et le mot de passe pour accéder à. |
| Impossible de télécharger l’application. Il manque des fichiers requis dans l’application. Contactez le fournisseur de l’application ou votre administrateur système. | Un ou plusieurs des fichiers répertoriés dans le manifeste d’application est introuvable sur le serveur. Vérifiez que vous avez téléchargé tous les fichiers de déploiement dépendants, puis réessayez. |
| Téléchargement de l’application n’a pas réussi. Vérifiez votre connexion réseau, ou contactez votre administrateur système ou votre fournisseur de services réseau. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Impossible d’établir une connexion réseau au serveur. Examiner la disponibilité du serveur et l’état de votre réseau. |
| URLDownloadToCacheFile a échoué avec HRESULT '\<nombre >'. Une erreur s’est produite lors de la tentative de téléchargement «\<fichier > ». | Si un utilisateur a la valeur option de fonctions avancées de sécurité Internet Explorer « Avertir des changements entre sécurisé et le mode non sécurisé » sur l’ordinateur cible de déploiement, et si l’URL d’installation de l’application ClickOnce en cours d’installation est redirigée à partir d’une non sécurisé vers un site sécurisé (ou vice versa), l’installation échoue, car l’avertissement Internet Explorer l’interrompra.<br /><br /> Pour résoudre cette erreur, vous pouvez effectuer l’une des tâches suivantes :<br /><br /> -Désactivez l’option de sécurité.<br />-Assurez-vous que l’URL d’installation n’est pas redirigé d’une manière qui modifie les modes de sécurité.<br />-Supprimer complètement la redirection et pointe vers l’URL d’installation proprement dit. |
| Une erreur s’est produite l’écriture sur le disque dur. Il peut être pas suffisamment d’espace disponible sur le disque. Contactez le fournisseur de l’application ou votre administrateur système. | Cela peut indiquer un espace disque insuffisant pour le stockage de l’application, mais il peut également indiquer une erreur d’e/s plus générale lorsque vous essayez d’enregistrer les fichiers d’application sur le lecteur. |
| Impossible de démarrer l’application. Ne comporte pas suffisamment d’espace disponible sur le disque. | Le disque dur est plein. Libérez de l’espace et essayez de réexécuter l’application. |
| Trop grand nombre d’activations déployées tente de charger en même temps. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] limite le nombre d’applications différentes qui peuvent démarrer en même temps. Il s’agit principalement pour vous protéger contre les tentatives malveillantes à provoquer des attaques par déni de service contre local [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] service ; les utilisateurs qui tentent de lancer la même application à plusieurs reprises, en succession rapide, revient à avec une seule instance de la application. |
| Raccourcis ne peut pas être activés sur le réseau. | Raccourcis vers un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application peut être démarrée uniquement sur le disque dur local. Ils ne peut pas être démarrées en ouvrant une URL qui pointe vers un fichier de raccourci sur un serveur distant. |
| L’application est trop grande pour exécuter en ligne avec une confiance partielle. Contactez le fournisseur de l’application ou votre administrateur système. | Une application qui s’exécute en confiance partielle ne peut pas être supérieure à la moitié de la taille du quota d’application en ligne, qui est de 250 Mo par défaut. |

## <a name="see-also"></a>Voir aussi
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Dépanner des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)