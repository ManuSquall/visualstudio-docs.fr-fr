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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699371"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensions chargées automatiquement de façon synchrone

Les extensions chargées de façon synchrone ont un impact négatif sur les performances de Visual Studio et doivent être converties pour utiliser le mode asynchrone asynchrone à la place. Par défaut, Visual Studio 2019 bloque les packages chargés de façon synchrone à partir de n’importe quelle extension et avertit l’utilisateur.

![Avertissement de compatibilité d’extension](media/extension-compatibility-warning-16-1.png.png)

Vous pouvez :

- Cliquez sur **autoriser le chargement synchrone** automatique pour autoriser les extensions à se synchroniser. Pour modifier ce paramètre dans les options de Visual Studio, cliquez sur environnement, sur extensions, puis cochez la case « Autoriser le chargement synchrone des extensions ». 

- Cliquez sur **gérer les performances** pour ouvrir la [boîte de dialogue Gestionnaire de performances](#performance-manager-dialog) qui affiche des problèmes de performances avec les extensions et les fenêtres outil.

- Cliquez sur **ne pas afficher ce message pour les extensions actuelles** pour ignorer la notification et empêcher les futures notifications des extensions installées existantes. Si vous ajoutez une nouvelle extension qui se charge de façon synchrone, cette notification s’affichera à nouveau. Vous continuerez à recevoir des notifications sur les autres fonctionnalités de Visual Studio.

## <a name="performance-manager-dialog"></a>Boîte de dialogue Performance Manager

![boîte de dialogue Performance Manager](media/performance-manager.png)

Toutes les extensions qui chargent de façon synchrone des packages dans toutes les sessions utilisateur s’affichent sous l’onglet **API déconseillées** .

* Cliquez sur **plus d’informations sur ce problème** pour recueillir plus d’informations sur les API déconseillées.
* Contactez leurs fournisseurs d’extension pour la progression de la migration.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Spécifier les paramètres de chargement synchrone à l’aide de la stratégie de groupe

Les administrateurs peuvent activer un stratégie de groupe pour autoriser le chargement synchrone synchrone. Pour ce faire, définissez une stratégie basée sur le Registre sur la clé suivante :

**HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Entrée = **autorisée**

Valeur = (DWORD)
* **0** est un autoload synchrone non autorisé
* **1** est une autoload synchrone autorisée

## <a name="extension-authors"></a>Auteurs d’extensions
Les auteurs d’extensions peuvent trouver des instructions pour la migration des packages vers le mode asynchrone asynchrone lors de la [migration vers AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Voir aussi
Pour plus d’informations sur les paramètres de chargement synchrone dans Visual Studio 2019, consultez la page [comportement synchrone de chargement](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) automatique.
