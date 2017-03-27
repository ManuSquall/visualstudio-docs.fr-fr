---
title: "Débogage à distance entre plusieurs plateformes avec Python Tools pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa667357-763f-4ce6-8e47-48f9337658a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 7634da4bdc2b0186f410acb4eaf57a70ddea3e91
ms.lasthandoff: 03/10/2017

---

# <a name="remotely-debugging-python-code"></a>Débogage à distance de code Python

Python Tools pour Visual Studio (PTVS) peut lancer et déboguer des applications Python localement et à distance sur un ordinateur Windows (consultez [Remote Debugging](../debugger/remote-debugging.md) (Débogage à distance)). Il peut également effectuer un débogage à distance sur un autre système d’exploitation, un appareil différent ou une implémentation Python autre que CPython à l’aide de la [bibliothèque ptvsd](https://pypi.python.org/pypi/ptvsd).

Lorsque vous utilisez ptvsd, le code Python faisant l’objet du débogage héberge le serveur de débogage auquel Visual Studio peut être attaché. Cela nécessite une petite modification de votre code pour importer et activer le serveur, et peut exiger des configurations du réseau ou du pare-feu sur l’ordinateur à distance pour autoriser les connexions TCP.

Pour une introduction au débogage à distance, visionnez la vidéo [Deep Dive: Cross-Platform Remote Debugging](https://youtu.be/y1Qq7BrV6Cc) (Expérience approfondie : Débogage à distance entre plusieurs plateformes ; youtube.com, 6 min22 s).

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="preparing-the-script-for-debugging"></a>Préparation du script pour le débogage

1. Créez un fichier Python avec le code suivant sur l’ordinateur distant :

  ```python
  import random

  guesses_made = 0
  name = raw_input('Hello! What is your name?\n')
  number = random.randint(1, 20)
  print 'Well, {0}, I am thinking of a number between 1 and 20.'.format(name)

  while guesses_made < 6:
      guess = int(raw_input('Take a guess: '))
      guesses_made += 1
      if guess < number:
          print 'Your guess is too low.'
      if guess > number:
          print 'Your guess is too high.'
      if guess == number:
          break
  if guess == number:
      print 'Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made)
  else:
      print 'Nope. The number I was thinking of was {0}'.format(number)
  ```
 
1. Installez le package `ptvsd` dans votre environnement à l’aide de `pip install ptvsd`.

1. Activez le débogage à distance en ajoutant le code ci-dessous au premier point possible dans le script, avant tout autre code. (Bien que cela ne soit pas strictement nécessaire, il est impossible de déboguer des threads en arrière-plan générés avant que la fonction `enable_attach` ne soit appelée.)

   ```python
   import ptvsd
   ptvsd.enable_attach(secret='my_secret')
   ```

   Le paramètre `secret` transmis à `enable_attach` est utilisé pour restreindre l’accès au script d’exécution. Lors de l’attachement, vous devrez spécifier ce paramètre dans Visual Studio ou la connexion sera refusée. Pour désactiver cette option et autoriser tout le monde à se connecter, utilisez `enable_attach(secret=None)`.

1. Enregistrez le fichier et démarrez le script sur l’ordinateur distant. Notez que l’appel à `enable_attach` s’exécute en arrière-plan et attend les connexions entrantes. Si vous le souhaitez, la fonction `wait_for_attach` peut être appelée après `enable_attach` pour bloquer le programme jusqu’à ce que le débogueur soit attaché.

En plus de `enable_attach` et `wait_for_attach`, ptvsd fournit une fonction d’assistance `break_into_debugger`, qui sert de point d’arrêt par programmation si le débogueur est attaché. Il existe également une fonction `is_attached` qui renvoie `True` si le débogueur est attaché (notez qu’il n’est pas nécessaire de vérifier ce résultat avant d’appeler d’autres fonctions `ptvsd`).

## <a name="attaching-remotely-from-python-tools"></a>Attachement à distance à partir de Python Tools

Dans ces étapes, nous allons définir un point d’arrêt simple pour arrêter le processus distant.

1. Créez une copie du fichier distant sur l’ordinateur local et ouvrez-le dans Visual Studio. L’emplacement du fichier importe peu, mais son nom doit correspondre au nom du script sur l’ordinateur distant auquel il sera attaché.

1. Sélectionnez **Déboguer > Attacher au processus** pour ouvrir la boîte de dialogue « Attacher au processus ».

1. Définissez **Transport** sur **Python remote debugging** (Débogage à distance Python).

1. Entrez l’adresse de l’ordinateur distant dans le champ **Qualificateur** et appuyez sur Entrée. Cette opération permet de répertorier les processus disponibles sur cet ordinateur :

![Saisie du qualificateur et énumération des processus](media/remote-debugging-qualifier.png)

1. Une erreur à ce stade indique généralement que le mot de passe ne correspondait pas, la version `ptvsd` ne correspond pas à celle utilisée par PTVS, ou une connexion n’a pas pu être établie. L’une des causes courantes d’échec de connexion est que l’ordinateur distant dispose d’un pare-feu qui bloque le port du serveur de débogage (5678 par défaut) ouvert. Vous pouvez reconfigurer le pare-feu ou utiliser un autre port ; cette opération peut être effectuée en le spécifiant explicitement dans l’appel à `enable_attach` dans le paramètre `address`, tel que :

  ```python
  ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))
  ```

  Le format d’adresse est le même que celui utilisé par le socket de module Python standard pour les sockets de type `AF_INET` ; consultez sa [documentation](http://docs.python.org/3/library/socket.html#socket-families) pour plus d’informations. 

1. Une fois que le processus s’affiche dans la liste, double-cliquez dessus pour l’attacher. Visual Studio affiche ses outils de débogage pendant que le script continue de s’exécuter. Pour l’exemple de script illustré ci-dessus, entrer un nombre permettra d’atteindre le point d’arrêt :

    ![Le point d’arrêt est atteint](media/remote-debugging-breakpoint-hit.png)

1. À ce stade, vous pouvez utiliser toutes les fonctionnalités de débogage de PTVS habituelles. 

1. Lorsque vous arrêtez le débogage, Visual Studio se détache de votre script, mais le script continue à s’exécuter sur l’ordinateur distant. Le serveur de débogage continue également l’exécution sur son thread en arrière-plan, donc vous pouvez attacher une nouvelle fois le processus ultérieurement en utilisant la même procédure.


## <a name="securing-the-debugger-connection-with-ssl"></a>Sécurisation de la connexion du débogueur avec SSL

Par défaut, la connexion au serveur de débogage à distance PTVS n’est pas sécurisée ; toute personne avec le mot de passe peut se connecter, et toutes les données sont transmises en texte brut. Par conséquent, d’autres utilisateurs du réseau peuvent fouiner dans les données ou même exécuter une attaque de type « Man-in-the-Middle ». Pour éviter ce problème, lors du débogage sur Internet ou des réseaux non sécurisés, le serveur de débogage prend en charge SSL. 

Pour sécuriser le canal avec SSL, vous aurez besoin d’un certificat SSL. Vous pouvez générer un certificat auto-signé vous-même, comme décrit dans la [documentation du module standard Python `ssl`](http://docs.python.org/3/library/ssl.html#self-signed-certificates). Pour empêcher les attaques de type « Man-in-the-Middle », un certificat généré devra également être ajouté au magasin racine de l’autorité de certification sur l’ordinateur Windows exécutant PTVS. Pour ce faire, vous pouvez utiliser le Gestionnaire de certificats (certmgr.msc) tel que décrit sur [How do I export certificates and/or private keys?](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/how-do-i-export-certificates-andor-private-keys/7722900a-e848-4076-bc50-9e2f5e3c66ac) (Comment puis-je exporter des certificats et/ou des clés privées ?). Notez que vous devrez disposer d’un fichier de certificat séparé (non associé à la clé privée dans un fichier unique) à importer. 

Une fois les fichiers de clé privée et de certificat générés et enregistrés, vous devrez mettre à jour l’appel à `enable_attach` dans votre script afin de les utiliser. Cette opération s’effectue au moyen des paramètres `certfile` et `keyfile`, qui ont la même signification que pour la fonction Python standard `ssl.wrap_socket`. Par exemple, si le fichier de certificat est appelé `my_cert.cer`, et si le fichier de clé est appelé `my_cert.key`, utilisez : 

```python
ptvsd.enable_attach(secret='my_secret', certfile='my_cert.cer', keyfile='my_cert.key')
```

Le processus d’attachement est exactement identique à celui décrit précédemment, sauf que, au lieu d’utiliser le schéma `tcp://` dans le champ Qualificateur, utilisez `tcps://` : 

![Choix du transport de débogage à distance avec SSL](media/remote-debugging-qualifier-ssl.png)

Si vous n’avez pas ajouté le certificat au magasin racine d’autorité de certification, vous obtiendrez un message d’avertissement : 

![Avertissement de certificat SSL](media/remote-debugging-ssl-warning.png)

Vous pouvez choisir d’ignorer cela et de poursuivre le débogage ; le canal sera chiffré contre les écoutes clandestines, mais ignorer l’avertissement présente un risque d’attaque de type « Man-in-the-Middle ».

