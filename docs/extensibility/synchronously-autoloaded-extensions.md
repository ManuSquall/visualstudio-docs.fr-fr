---
title: Extensions chargées automatiquement de façon synchrone
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab62d235fd6ed4e47e765fc23868acd5c56efcb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699371"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensions chargées automatiquement de façon synchrone

Les extensions rechargeables synchronously autoloaded ont un impact négatif sur les performances de Visual Studio et doivent être converties pour utiliser l’autocharge asynchrone à la place. Par défaut, Visual Studio 2019 bloque les paquets rechargeables de toute extension et en informe l’utilisateur.

![avertissement de compatibilité d’extension](media/extension-compatibility-warning-16-1.png.png)

Vous pouvez :

- Cliquez sur **Autoriser la recharge automatique synchrone** pour permettre des extensions à la charge automatique. Pour modifier ce paramètre dans les options Visual Studio, cliquez sur Environnement, puis cliquez sur Extensions, puis sélectionnez la case à cocher "Autoriser la charge automatique synchrone des extensions". 

- Cliquez sur **les performances de Gestion** pour ouvrir le dialogue Performance [Manager](#performance-manager-dialog) qui montre les problèmes de performance avec les extensions et les fenêtres d’outils.

- Cliquez sur Ne pas afficher ce message pour les **extensions actuelles** afin de rejeter la notification et d’empêcher les notifications futures des extensions installées existantes. Si vous ajoutez une nouvelle extension qui recharge rapidement, cette notification sera affichée à nouveau. Vous continuerez à recevoir des notifications sur d’autres fonctionnalités Visual Studio.

## <a name="performance-manager-dialog"></a>Dialogue de gestionnaire de performance

![dialogue de gestionnaire de performance](media/performance-manager.png)

Toutes les extensions qui chargent synchronisé les paquets dans toutes les sessions utilisateur apparaissent dans **l’onglet API déprécié.**

* Cliquez sur les **informations plus sur ce numéro** pour recueillir plus d’informations sur les API dépréciées.
* Contactez leurs fournisseurs de vulgarisation pour les progrès de la migration.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Spécifier les paramètres de chargement automatique synchrone à l’aide de la stratégie de groupe

Les administrateurs peuvent activer une politique de groupe pour permettre une recharge automatique synchrone. Pour ce faire, définissez une stratégie basée sur le Registre sur la clé suivante :

**HKEY_LOCAL_MACHINE-SOFTWARE-Policies-Microsoft-VisualStudio-SynchronousAutoload**

Entrée - **Permis**

Valeur = (DWORD)
* **0** est autocharge synchrone non autorisé
* **1** est autocharge synchrone permise

## <a name="extension-authors"></a>Auteurs de extension
Les auteurs d’extension peuvent trouver des instructions pour les paquets de migration à autocharge asynchrone à [Migre à AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Voir aussi
Pour plus d’informations sur les paramètres de recharge automatique synchrone dans Visual Studio 2019, consultez la page [Synchronous Autoload Behavior.](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/)
