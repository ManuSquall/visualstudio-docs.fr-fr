---
title: Configuration d’un dépôt Subversion
description: Utilisation de Subversion dans Visual Studio pour Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.topic: how-to
ms.openlocfilehash: ae67bdd9a9dac8daed268105d830064fa6ef4cae
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950417"
---
# <a name="set-up-a-subversion-repository"></a>Configurer un dépôt Subversion

Subversion est un _système de gestion de versions_ centralisé, ce qui signifie qu’il existe un seul serveur contenant tous les fichiers et révisions, à partir duquel les utilisateurs peuvent extraire n’importe quelle version de n’importe quel fichier. Quand les fichiers sont extraits d’un dépôt Subversion distant, l’utilisateur obtient une capture instantanée du dépôt à ce point dans le temps.

Pour utiliser Subversion pour la gestion de versions, vous devez l’installer sur votre ordinateur. Pour vérifier si Subversion est installé sur votre ordinateur, exécutez la commande suivante dans le Terminal :

```bash
svn --version
```

Cette commande retourne le numéro de version.

Si Subversion n’est pas encore installé, le moyen le plus simple de l’obtenir consiste à installer les _Outils en ligne de commande Xcode_. Exécutez la commande suivante pour installer les Outils en ligne de commande Xcode et Subversion.

```bash
xcode-select --install
```

Une fois Subversion installé sur votre ordinateur, effectuez les étapes suivantes pour publier votre projet dans SVN.

1. Créez un dépôt SVN gratuit en ligne. Pour cet exemple, [Assembla](https://app.assembla.com/) a été utilisé. Après la création, une URL est fournie, qui sera utilisée pour se connecter au dépôt :

    ![copier l’URL SVN](media/version-control-subversion1-sml.png)

2. Ouvrez ou créez un projet Visual Studio pour Mac.

3. Cliquez avec le bouton droit sur le projet et sélectionnez **Gestion de version > Publier dans la gestion de version...**  :

    ![Démarrer la publication d’un projet](media/version-control-subversion2.png)

4. Sous l’onglet **Se connecter au dépôt**, sélectionnez **Subversion** dans la liste déroulante du haut.

5. Entrez l’URL de l’étape 1. Une fois l’URL entrée, les autres champs sont renseignés par défaut :

    ![Boîte de dialogue Sélectionner un dépôt et entrer les détails](media/version-control-subversion3.png)

7. Cliquez sur **OK** puis confirmez en cliquant sur **Publier**.

7. Si vous y êtes invité, entrez vos informations d’identification pour le site sur lequel vous créez le dépôt, comme illustré ci-dessous :

    ![Entrée des informations d’identification pour le dépôt subversion](media/version-control-subversion5.png)

8. Toutes les commandes disponibles pour la gestion de versions doivent maintenant être visibles dans le menu Gestion de version.

## <a name="see-also"></a>Voir aussi

- [Utilisation de Subversion](working-with-subversion.md)