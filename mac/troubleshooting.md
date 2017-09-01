---
title: "Résolution des problèmes"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: a820423704b6f656b55b7e33f15d1c7880d2e27d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---

# <a name="troubleshooting"></a>Résolution des problèmes

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Affichage des journaux dans Visual Studio pour Mac
 
Vous pouvez trouver les journaux en accédant à l’élément de menu **Aide > Ouvrir le répertoire des journaux**, comme illustré ci-dessous :

![Élément de menu Ouvrir le répertoire des journaux](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Affichage des exceptions

Quand une exception a été interceptée, une bulle d’exception s’affiche. Pour afficher plus de détails, sélectionnez le bouton **Afficher les détails** :

![Afficher plus de détails sur une exception](media/troubleshooting-image2.png)

Ceci affiche la boîte de dialogue **Afficher les détails**, qui fournit plus d’informations sur l’exception :

![](media/troubleshooting-image3.png)

Voici les sections importantes de la boîte de dialogue, numérotées ci-dessus et décrites en détail ci-dessous :

1. Le type de l’exception, qui montre le nom complet du type de l’exception qui a été rencontrée.
2. Le message de l’exception, qui montre la valeur de la propriété Message de l’objet d’exception.
3. Le type d’exception interne, qui montre le nom complet du type d’exception pour l’exception actuellement sélectionné dans l’arborescence des exceptions internes.
4. Le message de l’exception interne, qui montre la valeur de la propriété Message de l’exception sélectionnée dans l’arborescence des exceptions internes.
5. Vue Stacktrace. Elle peut être réduit via une flèche commandant l’affichage et elle contient des entrées de frames de pile.
6. Exemple d’entrées de code non-utilisateur.
7. Exemple d’entrées de code utilisateur.
8. Vue Propriétés, qui montre toutes les propriétés et tous les champs de l’exception. Elle peut être réduite via une flèche commandant l’affichage.
9. Arborescence des exceptions internes Sélectionnez des exceptions internes dans cette vue via les flèches haut/bas du clavier, ou avec la souris ou le pavé tactile.
10. Par défaut, elle est définie d’après l’option **Déboguer uniquement le code du projet** définie dans les paramètres du débogueur. Le fait de cocher cette case permet la réduction de tout le code non-utilisateur à une seule ligne dans la trace de pile.
11. Un bouton Copier pour copier la sortie de `exception.ToString()` dans le Presse-papiers.

Notez que certaines de ces sections sont visibles seulement quand l’exception a une exception interne.
