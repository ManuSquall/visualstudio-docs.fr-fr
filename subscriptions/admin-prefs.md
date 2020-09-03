---
title: Définir les préférences des contrats dans le portail d’administration
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 03/17/2020
ms.topic: conceptual
description: Découvrir comment définir les préférences pour la langue, les contacts, le niveau d’abonnement et d’autres éléments dans le portail d’administration
ms.openlocfilehash: e34b9cf1ed32abc81b9c2ebb3ef7c370818c9089
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87234612"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Définir les préférences pour vos contrats dans le portail d’administration
Les super administrateurs peuvent définir certaines préférences dans le portail d’administration (portail d’administration) qui seront appliquées globalement pour chaque contrat.  Ces préférences remplissent automatiquement les détails de l’abonnement pour vos administrateurs lorsqu’ils ajoutent des abonnés et peuvent uniquement être modifiées globalement par les super administrateurs.  

## <a name="access-preferences"></a>Accéder aux préférences
Vous devez être connecté au [portail d’administration](https://manage.visualstudio.com) avec un ID de connexion disposant de droits de super administrateur sur le contrat pour pouvoir consulter ou modifier les préférences.  

Pour définir vos préférences :
1. Connectez-vous au portail d’administration avec un ID disposant de privilèges de super administrateur.
2. Cliquez sur l’onglet **Gérer les administrateurs**.
   > [!div class="mx-imgBorder"]
   > ![Bouton Préférences pour les administrateurs](_img/admin-prefs/admin-prefs-button.png "Cliquez sur gérer les administrateurs, puis sur Préférences d’accord pour afficher les préférences")

3. Cliquez sur **Préférences des contrats**.
Un panneau s’ouvre à droite et les préférences disponibles s’affichent. 

   > [!div class="mx-imgBorder"]
   > ![Boîte de dialogue du menu volant Préférences pour les administrateurs](_img/admin-prefs/admin-prefs-flyout.png "Définissez vos préférences, puis cliquez sur Enregistrer")

## <a name="set-your-preferences"></a>Définir vos préférences
Nous allons explorer chacune des préférences disponibles et leurs effets. 

### <a name="agreement"></a>Contrat
Si vous avez plusieurs contrats pour lesquels vous êtes super administrateur, vous pouvez choisir le contrat souhaité dans la liste déroulante.  Les préférences que vous définissez s’appliquent seulement à ce contrat.  Les administrateurs individuels peuvent remplacer certaines de ces préférences au cas par cas lors de l’attribution des abonnements. 

S’il n’existe qu’un seul contrat associé à l’adresse e-mail que vous avez utilisée pour vous connecter, il est affiché et la liste déroulante est désactivée. 

### <a name="contact-email-address"></a>Adresse e-mail de contact
Cette préférence permet à vos abonnés d’accéder aux administrateurs à l’aide du bouton **contacter mon administrateur** sur la [page abonnements](https://my.visualstudio.com/subscriptions) du portail de l’abonné.  Si cette préférence est laissée vide, les messages de l’abonné sont transférés à tous les administrateurs et tous les super administrateurs du contrat.  Nous vous recommandons d’utiliser un alias d’e-mail de groupe ou un groupe de sécurité pour adapter votre audience à cet e-mail de contact. Si vous préférez, vous pouvez aussi choisir d’entrer l’adresse e-mail d’une personne.

> [!NOTE]
> L’adresse e-mail que vous indiquez ici n’est PAS fournie aux abonnés.  Lorsqu’un abonné soumet une demande de **contact avec mon administrateur** dans le portail de l’abonné, le message est transféré à l’alias sans l’exposer à l’abonné. 

### <a name="default-external-subscribers-setting"></a>Paramètre des abonnés externes par défaut
Cette préférence vous permet de décider si les administrateurs peuvent ajouter des abonnés extérieurs au locataire/annuaire de votre organisation.  Si vous désactivez cette option, aucun abonné externe n’est autorisé.  Si vous l’activez et qu’un administrateur tente d’ajouter un abonné externe, il est invité à confirmer son choix, puis est autorisé à attribuer l’abonnement. Les administrateurs ne peuvent pas remplacer ce paramètre. 

### <a name="default-downloads-setting"></a>Paramètre des téléchargements par défaut
L’activation de ce paramètre, qui est activé par défaut, permet aux abonnés d’accéder aux téléchargements quand les administrateurs créent des abonnements.  Les administrateurs peuvent néanmoins toujours désactiver les téléchargements sur la base d’un abonnement individuel.  La désactivation de l’accès aux téléchargements désactive également l’accès aux clés de produit.  

### <a name="default-subscription-level"></a>Niveau d’abonnement par défaut
Vous pouvez utiliser ce paramètre pour déterminer quel niveau d’abonnement inclus dans votre contrat est sélectionné par défaut quand un abonnement est attribué à un utilisateur.  Les administrateurs peuvent changer le paramètre et le définir sur n’importe quel niveau d’abonnement de votre contrat : ceci vous évite simplement d’avoir à effectuer de façon répétée votre choix le plus courant. 

### <a name="default-communication-preferences"></a>Préférences de communication par défaut
La définition de la langue et des paramètres régionaux de communication par défaut permet de simplifier le processus d’attribution des abonnements.  Par exemple, si votre équipe de développement est basée dans un pays différent de celui de votre équipe d’administration, vous pouvez définir les préférences les mieux adaptées à l’emplacement des abonnés. Ces paramètres peuvent néanmoins toujours être modifiés par tous les administrateurs pour des abonnés individuels. 

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>Q : puis-je désactiver l' **adresse de messagerie du contact** afin que les abonnés ne puissent pas contacter les administrateurs ?
R : non-si vous pouvez déterminer quels administrateurs sont contactés à l’aide d’un groupe de sécurité, d’un alias de messagerie de groupe ou d’une adresse de messagerie individuelle, la fonctionnalité ne peut pas être désactivée.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>Q : si je réponds à l’e-mail d’un abonné, est-ce qu’il a mon adresse de messagerie ?
R : étant donné que votre réponse provient du client de messagerie que vous utilisez, la réponse que l’abonné reçoit affiche l’adresse e-mail que vous utilisez.  Ainsi, si vous répondez depuis un alias de groupe, l’abonné voit l’alias de groupe.  Si vous répondez depuis votre propre adresse e-mail, il voit cette adresse.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>Q : où puis-je en savoir plus sur la fonctionnalité **contacter mon administrateur** dans le portail de l’abonné ?
R : consultez notre article [contacter mon administrateur](contact-my-admin.md) . 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>Q : si l' **adresse de messagerie du contact** n’est pas complétée et qu’un abonné utilise la fonctionnalité **contacter mon administrateur** , qui reçoit sa demande ?
R : si aucune adresse de messagerie spécifique n’est définie dans la préférence de l' **adresse de messagerie du contact** , tous les administrateurs de l’accord reçoivent la demande. 

## <a name="resources"></a>Ressources
- [Prise en charge des abonnements et de l’administration de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur la gestion des abonnements Visual Studio.
- [Affecter des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)
