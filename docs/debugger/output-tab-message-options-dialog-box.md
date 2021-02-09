---
title: Onglet sortie de la boîte de dialogue Options des messages | Microsoft Docs
description: Utilisez l’onglet sortie des options de message pour spécifier les données de message qui s’affichent dans la vue messages. Cet article décrit les paramètres disponibles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Output
ms.assetid: 22dd48c2-6d17-41b1-b84c-9ddeaef68411
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9cb48f061cfda78e3dec8ef515df82fdefb8193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891577"
---
# <a name="output-tab-message-options-dialog-box"></a>Onglet Sortie de la boîte de dialogue Options des messages
Utilisez l’onglet **sortie** pour spécifier les données de chaque message à répertorier dans la [vue messages](../debugger/messages-view.md). Pour afficher la [boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md), choisissez **journaux des messages** dans le menu **Espion** .

 Les paramètres suivants sont disponibles sous l’onglet **sortie** :

 **Numéros de ligne** Affichez les numéros de ligne.

 **Niveau d’imbrication des messages** Préfixez les messages imbriqués avec un point par niveau.

 **Paramètres de messages bruts** Affichez les valeurs hexadécimale **wParam** et **lParam** .

 **Paramètres de messages décodés** Affichez les résultats du décodage spécifique au message des valeurs **wParam** et **lParam** .

 **Valeurs de retour brutes** Affichez la valeur de retour de **LRESULT** hexadécimale.

 **Valeurs de retour décodées** Affichez les résultats du décodage spécifique au message de la valeur de retour **LRESULT** .

 **Heure d’origine du message** Temps écoulé depuis le démarrage du système Windows (uniquement pour les messages publiés).

 **Position de la souris du message** Coordonnées d’écran de la souris lorsque le message a été publié (uniquement pour les messages publiés).

 **Lignes au maximum** Limitez le nombre de lignes conservées dans la vue messages actuellement sélectionnés.

 **Enregistrer également les messages dans un fichier** Spécifiez un fichier de sortie pour le journal des messages. Ce fichier de sortie est écrit simultanément avec la fenêtre du journal des messages.

 **Enregistrer les paramètres par défaut** Enregistrez les paramètres précédents pour les nouvelles fenêtres de flux de messages. Ces paramètres sont enregistrés lorsque vous quittez Spy + +.