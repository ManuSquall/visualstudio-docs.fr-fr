---
title: 'Zone de test 2 : récupérer à partir du contrôle de code source | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 069c396ce4cb75c9153082fdbb352b2ba713c8a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156008"
---
# <a name="test-area-2-get-from-source-control"></a>Zone de test 2 : Obtenir à partir du contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette zone de test couvre les cas de test permettant de récupérer des éléments de la Banque des versions à l’aide de la commande obtenir. Ces cas de test peuvent être appliqués aux projets locaux et aux projets Web.  
  
## <a name="command-menu-access"></a>Accès au menu commande  
 Les [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] chemins d’accès au menu de l’environnement de développement intégré suivants sont utilisés dans les cas de test.  
  
##### <a name="get-latest-version"></a>Télécharger la dernière version :  
  
- **Fichier**, **contrôle de code source**, **Télécharger la dernière version**.  
  
- **Fichier**, **Télécharger la dernière version**.  
  
- Menu contextuel, **récupérer la dernière version**.  
  
- Obtient : **fichier**, **contrôle de code source**, **récupérer**.  
  
## <a name="expected-behavior"></a>Comportement attendu  
  
##### <a name="get-latest-version"></a>Télécharger la dernière version :  
 Effectue une récupération en mode silencieux (sans interface utilisateur) de la dernière version de l’élément à partir de la Banque des versions.  
  
##### <a name="get"></a>Obtenir :  
 Affiche la boîte de dialogue **recevoir** et permet à l’utilisateur d’apporter des modifications au jeu de fichiers qui sera récupéré, ainsi que de modifier les options qui affectent la façon dont les fichiers sont récupérés.  
  
## <a name="test-cases"></a>Cas de test  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Obtenir la dernière version d’un fichier qui n’existe pas localement|1. Créez un projet.<br />2. Ajoutez un élément au projet.<br />3. Placez le projet sous le contrôle de code source.<br />4. supprimer la copie locale de l’élément.<br />5. Procurez-vous la dernière version de l’élément (menu contextuel, **récupérez la dernière version**).|Le fichier d’élément est récupéré localement.|  
|Obtenir un fichier qui n’existe pas localement|1. Créez un projet.<br />2. Ajoutez un élément au projet.<br />3. Placez le projet sous le contrôle de code source.<br />4. supprimer la copie locale de l’élément.<br />5. récupération de l’élément (**fichier**, **contrôle de code source**, **récupération** \<item> ).|Le fichier d’élément est récupéré localement.|  
|Obtenir un fichier qui a été extrait en mode exclusif et modifié localement|1. Créez un projet.<br />2. Ajoutez un élément au projet.<br />3. Placez le projet sous le contrôle de code source.<br />4. consultez l’élément de projet en mode exclusif.<br />5. modifiez la copie locale.<br />6. Procurez-vous la dernière version de l’élément (**fichier**, procurez-vous la **dernière version de** \<item> ). Si cette étape se déroule correctement, passez à l’étape suivante.<br />7. cliquez sur le bouton **remplacer** dans la boîte de dialogue d’avertissement.|**Résultat de l’étape 6**`:`<br /><br /> La boîte de dialogue d’avertissement indique que le fichier est extrait.<br /><br /> **Résultat de l’étape 7 :**<br /><br /> Le fichier local modifié est remplacé par la version d’origine de la Banque des versions.<br /><br /> Le fichier est en lecture/écriture.|  
|Récupérer et remplacer un fichier qui est extrait, partagé et modifié localement|1. Créez un nouveau projet.<br />2. Ajoutez un élément au projet.<br />3. Placez le projet sous le contrôle de code source.<br />4. Extrayez l’élément de projet comme étant partagé.<br />5. modifiez la copie locale.<br />6. Procurez-vous la dernière version de l’élément (**fichier**, procurez-vous la **dernière version de** \<item> ). Si cette étape se déroule correctement, passez à l’étape suivante.<br />7. cliquez sur **remplacer** dans la boîte de dialogue d’avertissement.|**Résultat de l’étape 6 :**<br /><br /> La boîte de dialogue d’avertissement indique que le fichier est extrait.<br /><br /> **Résultat de l’étape 7 :**<br /><br /> Le fichier local modifié est remplacé par la version d’origine de la Banque des versions.<br /><br /> Le fichier est en lecture/écriture.|  
|Obtenir un fichier qui existe localement, identique à la dernière version dans la Banque des versions|1. Créez un nouveau projet.<br />2. Ajoutez un élément au projet.<br />3. Placez le projet sous le contrôle de code source.<br />4. récupération de l’élément (**fichier**, **contrôle de code source**, **récupération** \<item> ).|Le fichier local est inchangé.|  
|Obtenir une solution avec un seul projet|1. Créez une solution avec un projet.<br />2. Placez la solution sous contrôle de code source.<br />3. Supprimez tous les fichiers projet localement.<br />4. récupérez la solution (**fichier**, **contrôle de code source**, **extraire**).|Tous les fichiers supprimés sont restaurés localement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
