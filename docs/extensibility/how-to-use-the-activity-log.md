---
title: 'Procédure : utiliser le journal d’activité | Microsoft Docs'
description: Les VSPackages peuvent écrire des messages dans le journal d’activité. Découvrez comment utiliser le journal d’activité pour déboguer les VSPackages dans les environnements de vente au détail.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f02a8dd1497680239db9363a2e0682082f0c68d8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057336"
---
# <a name="how-to-use-the-activity-log"></a>Procédure : utiliser le journal d’activité
Les VSPackages peuvent écrire des messages dans le journal d’activité. Cette fonctionnalité est particulièrement utile pour déboguer les VSPackages dans les environnements de vente au détail.

> [!TIP]
> Le journal d’activité est toujours activé. Visual Studio conserve une mémoire tampon enchaînée des 100 dernières entrées, ainsi que les 10 premières entrées, qui contiennent des informations de configuration générales.

## <a name="to-write-an-entry-to-the-activity-log"></a>Pour écrire une entrée dans le journal d’activité

1. Insérez ce code dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode ou dans toute autre méthode, à l’exception du constructeur VSPackage :

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Ce code obtient le <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service et le convertit en une <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> écrit une entrée d’information dans le journal d’activité à l’aide du contexte culturel actuel.

2. Lorsque le VSPackage est chargé (généralement lorsqu’une commande est appelée ou qu’une fenêtre est ouverte), le texte est écrit dans le journal d’activité.

## <a name="to-examine-the-activity-log"></a>Pour examiner le journal d’activité

1. Exécutez Visual Studio avec le commutateur de ligne de commande [/log](../ide/reference/log-devenv-exe.md) pour écrire des ActivityLog.xml sur le disque au cours de votre session.

2. Après la fermeture de Visual Studio, recherchez le journal d’activité dans le sous-dossier pour les données Visual Studio :

   <em> *% AppData%</em>\Microsoft\VisualStudio \\ \<version>\ActivityLog.xml*.

3. Ouvrez le journal d’activité avec n’importe quel éditeur de texte. Voici une entrée typique :

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Programmation fiable

Étant donné que le journal d’activité est un service, le journal d’activité n’est pas disponible dans le constructeur VSPackage.

Vous devez obtenir le journal d’activité juste avant de l’écrire. Ne mettez pas en cache ou n’enregistrez pas le journal d’activité pour une utilisation ultérieure.

## <a name="see-also"></a>Voir aussi

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Dépannage de VSPackages](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)
