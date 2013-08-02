*********************
Having a usable |vim|
*********************

This is maybe a surprising approach for you, but for me, the first thing to do is to have a |vim| usable by a normal human being. It seems that everybody agrees that |vim| is a very **powerful editor**. And I think that you will agree too if I say that, by default, |vim| is totally unusable. Let's be honest, without a decent minimal configuration, using |vim| is **counterproductive**.

In my humble opinion, it's the first obstacle to tackle before anything else. This is what all the trendy editors like TextMate, Sublime Text, Notepad++ or Netbeans are proposing: a default environment usable as it is, even if we don't use its full potential for now.

Here is what a default |vim| is missing (and why **most of people are giving up** before they can really see the power of |vim|):

**Default configuration**
    You can configure |vim| thanks to a file named |vimrc|. This file is, obviously, totally empty by default. The first thing to do will be to have a |vimrc| file with a minimal configuration.

**Syntax highlighting**
    By default, |vim| is white and ugly. To fix that, we will use the `Solarized theme <http://ethanschoonover.com/solarized>`_. If your goal is to be efficient, it's the best theme available out there (across all text editors), period. The beautiful image below will give you an idea of what it looks like (with the dark and the light theme). Personally, I'm using the dark theme.

    |solarized|

.. |solarized| image:: ../book-tex/graphics/solarized-yinyang-mini.png

**File explorer**
    If your are using |vim| along with a graphical interface (I suppose it's the case for 99% of you) you will by default have a ``File`` menu available. This menu should allow you to open a file. It's, for sure, a good start. But having a file explorer a la Netbeans or Textmate can be very handy. To mimic the same behavior, we will be using `The NERD Tree <http://www.vim.org/scripts/script.php?script_id=1658>`_. Be aware that, once you will have read this guide, you will not need the mouse anymore.


This chapter is mandatory if you have very few (or not at all) experience with |vim|. By the end of the chapter, you will have a |vim| usable on a daily basis. It should be enough to then be able to learn it gradually. Because, of course, there is no magic, you will have to practice to be able to learn |vim|, the sooner, the better.

However, if your are already familiar with |vim| and don't use the mouse anymore, you can skip this chapter. But be sure to give *Solarized* a try, you would be missing something otherwise.


.. _modeinsertion:

Essential preamble: the insert mode
===================================

Let's be totally crazy. We will try to create the |vimrc| configuration file with |vim| itself. As I said earlier, the sooner you start to use |vim|, the better. I told you it would be totally crazy.

The first thing to do will certainly be to install a |vim| version for your operating system. If you are using a Mac, give `MacVim <http://code.google.com/p/macvim/>`_ a try, it's the best |vim| port for Mac without any doubt. If your are using GNU/Linux or any other "Unix-like" system, you should have *gVim* available, or at least easily installable using your package management system. For Windows, it seems that there is a version available on the official |vim| website (http://www.vim.org/download.php), but I did not test it.

When you will start |vim|, you should see a welcome text asking you to help poor children in Uganda. 

.. image:: ../book-tex/graphics/vim-uganda.png

This text will disappear as soon as we will be writing text in |vim|. 

We will start by adding a comment in the header of the file to specify the author of the document (should be you). To be able to type text, the first thing to do will be to press |tti| (the cursor should have changed). The welcome text should have disappeared and you should have `a blank page`_ looking like the image below:

.. _a blank page:

.. image:: ../book-tex/graphics/vim-new.png

**On a side note**: if you don't really understand what you did and |vim| is displaying red messages at the bottom left or doesn't seem to react as it should when your pressing |tti|, don't panic. Pressing multiples times on |ttesc| (two times should be enough) should bring |vim| to its default mode, the *Normal mode*. Then it should behave as you would expect again.

You should know be able to write down `the comment below`_:

.. _the comment below:

::

    " VIM Configuration - Vincent Jousse

You will have noticed that comments in *VimL* (the name of the |vim| programing language) start with a :viml:`"`. Then press |ttesc| to come back to the default mode (the normal mode) of |vim|. That's all, you are done. Here is a screenshot of what your |vim| should look like now:

.. image:: ../book-tex/graphics/vim-first-comment.png

I can already hear you: all that fuss for what? Well, yes. And you even don't know how to save a file. But all these things are logical that I'm gonna explain to you. One of the advantages of |vim| is that, usually, it is logical. Once you will have understood the logic behind it, all will be crystal clear for you (at least I hope).

By default, when you start |vim|, you are presented with its default mode. This mode is called the *Normal mode*. The purpose of this mode is not to write text (for that, you will have the *Insert mode*), but only to move the cursor and to manipulate text. The power of |vim| is coming from the combination of these two modes (other modes exist, but it's not the topic for now). You will need some time and some practice to realize the power it's giving to you, so you will just need to trust me in the meantime.

If you are asking yourself why those modes, why by default we can't even write down some text and why we are making things more complicated than they should, the next chapter is for you.

.. _modes:

Modes: the powerful |vim| secrets
=================================

I suppose you will agree if I say that, if you want to learn |vim|, it's to be more efficient when writing/manipulating text or code. To be more efficient when writing text, there is not many solutions. There is only one actually: you need to move your hands as less as you can (even not at all) and only move your fingers.

To do so, of course, you will need to do without your mouse. In addition to being slow, the move keyboard -> mouse and then mouse -> keyboard is really bad for your articulations. It's often the cause of musculoskeletal disorders. Maybe you are still young and don't know what I'm talking about. But believe me, you will have such problems one day or another (often sooner than what you think). If your are in front of your computer all day long, don't neglect those possible troubles, you may regret it someday. `According to Wikipedia <http://en.wikipedia.org/wiki/Musculoskeletal_disorder>`_, it's actually the most common professional disease.

You will need to forget the move of your right hand toward the directional keys (left/right/bottom/top) too. It's a waste of time and it's completely unneeded with |vim|.

So what do you have the right to do? Not a lot to be honest (but it's for your own good), you can only leave your hands on the home row `as you can see on the picture below`_.

.. _as you can see on the picture below:

.. figure:: ../book-tex/graphics/hand-position.png
   
   Home row, QWERTY keyboard

   *Illustration by Cy21 - CC-BY-SA-3.0* (http://www.creativecommons.org/licenses/by-sa/3.0) or GFDL (http://www.gnu.org/copyleft/fdl.html), via Wikimedia Commons http://commons.wikimedia.org/wiki/File:Typing-home-keys-hand-position.svg

You will also find on each keyboard some marks on the letters F and J, the goal of these marks is to give a landmark for the position of your fingers (the indexes) on the home row of the keyboard.

Trying to move as less as possible the hands from the keyboard is the reason for having a *normal* mode and an *insert* mode in |vim|. When switching from one to the other, the keys under your fingers will sometimes allow you to move the cursor and to manipulate text: copy/paste, deletion, … (it's the normal mode), sometimes they will allow you to select some text (it's the *visual mode*) and sometimes to insert some text (it's the *insert* mode). And of course, all of that is possible without the extensive use of keys combinations like *Ctrl + key* that are very bad for your fingers (*Emacs*, this on is for you).

By default, we can switch from the *insert* mode to the *normal* mode by pressing |ttesc|, but it will be one of the first things we will change: |ttesc| is to far from your fingers on actual keyboards.

To switch from *normal* mode to *insert* mode, we can for example press |tti|. We will later learn that there are other ways to do so too. For example, to enter the *insert* mode and to then create a new line below the current one (no matter where is your cursor on the line), we will use |tto| while in *normal* mode.

I will talk again about this subject later in ":ref:`se-deplacer`", but if your are not ready, at some point, to do without your mouse and the directional keys to edit text, I would recommend you to stop learning |vim| right now. It's as simple as that. You can leverage the full power of |vim| only by getting rid of the mouse and by moving your hand as little as possible.

If you want to go further, you can buy an orthogonal keyboard like `TypeMatrix <http://www.typematrix.com>`_. It's the keyboard I'm currently using, and my fingers are thanking me everyday.

The ultimate change would be to switch your keyboard layout to a more efficient one like `Colemak <http://colemak.com/>`_. But it's another story.


The life saver default configuration
====================================

Let's get serious, let's try to have a usable |vim|. We will start by editing the default configuration file |vimrc| and by entering default values that any sane guy would love to find in it.

You have to place this file in your home directory. It should be */home/your_user/.vimrc* if your are using Linux, */Users/your_user/.vimrc* if your are using Mac OS X. Generally speaking, it should be in you home directory under *~/.vimrc*. If you are using Windows, you can create a file named *_vimrc* that you have to put in your *%HOME%* directory. This directory is obviously not the same across the different Windows versions. Usually, it the directory just before your directory *My Documents*. More information is `available on Wikipedia <http://en.wikipedia.org/wiki/Home_directory#Default_Home_Directory_per_Operating_System>`_ if you want.


I've directly commented all the lines in the code itself. Nothing fancy here, you should just be asking yourself why all of this is not available by default.

.. include:: ../../vim-for-humans/firstconfig/vimrc
   :code:


Pour ceux qui ont fait un copier/coller, il ne vous reste plus qu'à sauvegarder votre fichier nouvellement créé. Nous voulons le placer à la racine de votre compte utilisateur, c'est à dire l'enregistrer sous `~/.vimrc`. Sous Mac OS X et Linux, *~* désigne le répertoire d'accueil de l'utilisateur courant. Attention, les fichiers commençant par un ``.`` sont des fichiers cachés sous Linux et Mac OS X, ne vous étonnez donc pas de ne pas le voir par défaut dans votre navigateur de fichiers.

Pour les utilisateurs de la souris, il suffira de se servir du menu `Fichier (ou File)` puis `Sauvegarder sous (ou Save as)` et de l'enregistrer dans le répertoire d'accueil de l'utilisateur courant sous le nom de `.vimrc`. Pour ceux qui veulent déjà utiliser le clavier, il vous suffira, après avoir appuyé sur |ttesc| pour repasser en mode *Normal*, de taper :vimcmd:`:sav ~/.vimrc`. Pour sauvegarder vos prochaines modifications, utilisez le menu avec la souris ou tapez en mode *Normal* :vimcmd:`:w`.

J'ai mis en ligne ce fichier de configuration directement sur *Github*. Vous pouvez le télécharger ou le copier directement à partir d'ici : http://vimebook.com/link/fr/firstconfig.

Voici à quoi devrait ressembler |vim| `après votre première configuration`_.


.. _après votre première configuration:

.. figure:: ../book-tex/graphics/vim-first-config.png

   |vim| après votre première configuration.

Notez les numéros de ligne sur la gauche ainsi que la position du curseur en bas à droite.

Bon c'est bien beau tout ça mais ça manque un peu de couleurs. Au suivant !

Que la couleur soit !
=====================

Tout d'abord il faut commencer par activer la coloration syntaxique du code dans le fichier de configuration. Ajoutez ces lignes à là fin de votre fichier de configuration |vimrc|.::

    " Active la coloration syntaxique
    syntax enable
    " Active les comportements specifiques aux types de fichiers comme
    " la syntaxe et l'indentation
    filetype on
    filetype plugin on
    filetype indent on

Vous devriez avoir un |vim| qui ressemble à celui de la figure ci-dessous. 


.. figure:: ../book-tex/graphics/vim-syntax-hl.png

   Coloration syntaxique par défaut.

Pour l'instant, le plus facile pour que les modifications apportées à votre |vimrc| soient prises en compte, c'est de le fermer et de le ré-ouvrir. Si vous voulez vraiment vous la jouer à la |vim| de suite, en mode normal tapez :vimcmd:`:so ~/.vimrc` ou :vimcmd:`:so $MYVIMRC`.

:vimcmd:`:so` étant un raccourci pour :vimcmd:`:source`. C'est une bonne première étape, passons maintenant à l'utilisation d'un thème.

Les thèmes vont vous permettre de rendre votre |vim| un peu moins austère en changeant généralement la couleur de fond ainsi que les couleurs par défaut pour le code. Comme je l'ai mentionné plus haut, nous allons utiliser le thème *Solarized* http://ethanschoonover.com/solarized (avec fond clair ou foncé, ça dépendra de vous).

Pour l'installer, commencez tout d'abord par créer un répertoire nommé `.vim` au même endroit que votre |vimrc| (dans votre répertoire utilisateur donc). À noter que ce répertoire s'appelle `vimfiles` sous Windows. À chaque fois que je ferai référence au répertoire `.vim` ça sera en fait `vimfiles` pour les Windowsiens. Dans ce répertoire `.vim`, créez un sous-répertoire nommé `colors`. Téléchargez ensuite le fichier du thème *Solarized* https://raw.github.com/altercation/vim-colors-solarized/master/colors/solarized.vim (c'est le même fichier pour les deux versions du thème) et copiez le dans le répertoire `vim/colors/` fraîchement créé. Votre répertoire `.vim` devrait ressembler à celui de la figure ci-dessous.

.. figure:: ../book-tex/graphics/solarized-tree.png

   Le contenu du répertoire .vim avec Solarized.

Activez ensuite le thème Solarized dans votre |vimrc| comme le montre le code ci-dessous.::

    " Utilise la version sombre de Solarized
    set background=dark
    colorscheme solarized

Pour tester le thème clair, remplacez `dark` par `light` (au niveau de la définition de la propriété `background`).

Ci-dessous un aperçu des deux variantes (ma préférence allant à la variante sombre soit dit en re-passant).

.. figure:: ../book-tex/graphics/vim-solarized-dark.png

   Le thème *Solarized* sombre.


.. figure:: ../book-tex/graphics/vim-solarized-light.png

   Le thème *Solarized* clair.


Un bonus (si vous n'utilisez pas |vim| directement dans votre terminal) serait de choisir une police de caractères qui vous convient un peu mieux. C'est bien sûr facultatif, mais je présume que certains d'entre vous sont des esthètes aguerris.

Si vous êtes sous Mac OS X je vous conseille la police `Monaco` qui est assez conviviale. Rajoutez les lignes suivantes à votre |vimrc| pour l'utiliser : ::

    set guifont=Monaco:h13
    set antialias

Vous pouvez bien sûr changer le `h13` par `h12` si vous voulez une police plus petite (ou par `h14` si vous en voulez une plus grande).

Sinon sous Linux j'utilise la police `DejaVu Sans Mono` que je trouve plutôt sympathique : ::

    set guifont=DejaVu\ Sans\ Mono\ 10
    set antialias

Vous pouvez là aussi bien sûr changer la taille de la police si vous le souhaitez. Pour avoir la liste des polices disponibles tapez en mode normal :vimcmd:`:set guifont:*`.

Vous trouverez une version complète du fichier de configuration pour ce chapitre en ligne http://vimebook.com/link/fr/syntaxhlconfig. Je ne m'attarderai pas plus sur les polices, c'est assez dépendant de votre système d'exploitation, et un peu moins de |vim|.


L'explorateur de fichiers : notre premier plugin
================================================

Nous y voilà, nous avons un |vim| à peu près utilisable avec de jolies couleurs. Maintenant, il faudrait être capable d'ouvrir des fichiers autrement qu'en faisant `Fichier (File) -> Ouvrir (Open)`. Ça va être une bonne occasion pour installer notre premier plugin (ce n'est pas comme si nous avions d'autres choix de toute façon). Nous allons procéder ici en deux étapes, tout d'abord installer un gestionnaire de plugins pour éviter que ça devienne trop le bazar dans vos plugins, puis installer le plugin adéquat pour explorer un répertoire de fichiers.

Gestionnaire de plugins: Pathogen
---------------------------------

*Pathogen* (https://github.com/tpope/vim-pathogen/) est le genre de plugin typique que vous découvrez après avoir commencé à configurer votre |vim| et qui génère ce type de réaction : « Ah si j'avais su j'aurais directement commencé avec ». Ça tombe bien, c'est ce que nous allons faire.

Tout d'abord, petite explication sur la manière d'installer et de configurer des plugins dans |vim|. Ils s'installent en copiant les fichiers adéquats (la plupart du temps avec une extension en *\*.vim*) dans des sous-répertoires de votre répertoire de configuration *.vim*. On a déjà d'ailleurs commencé à y créer un sous-répertoire `colors` qui contient notre "plugin" de coloration Solarized.

Le problème avec cette approche c'est que les différents plugins ne sont pas isolés (vous allez devoir copier leurs fichiers dans les différents sous-répertoires) et que vous allez donc vous retrouver avec des fichiers un peu partout sans savoir à qui ils appartiennent. Autant vous dire qu'une fois que vous voulez désinstaller ou mettre à jour un plugin, c'est vite l'enfer pour savoir quels sont ses fichiers.

C'est là que *Pathogen* arrive à la rescousse, il va vous permettre d'installer chaque plugin dans un sous-répertoire rien que pour lui. Voici un exemple de répertoire `.vim` avant et après l'utilisation de *Pathogen*. 

.. figure:: ../book-tex/graphics/pathogen-tree.png

   *.vim* avant et après Pathogen.

Certes la version avec *Pathogen* contient plus de sous-répertoires, mais croyez-moi sur parole, ce rangement va vous éviter bien des ennuis par la suite. Vous pourrez au passage très facilement utiliser *git* pour gérer chacun de vos plugins comme des submodules, ce qui peut s'avérer très pratique.

Commençons par installer *Pathogen*. Créez un répertoire nommé `autoload` dans votre répertoire `.vim` et copiez y `pathogen.vim` que vous pouvez télécharger ici : https://raw.github.com/tpope/vim-pathogen/master/autoload/pathogen.vim. Pour les utilisateurs Unix, le listing qui suit explique comment l'installer. Si vous n'avez pas `curl` vous pouvez aussi utiliser `wget -O -`.

.. code-block:: bash

    # Creation du repertoire autoload
    mkdir -p ~/.vim/autoload 

    # Telechargement et installation de pathogen
    curl -so ~/.vim/autoload/pathogen.vim \
        https://raw.github.com/tpope/vim-pathogen/master/autoload/pathogen.vim

Nous installerons ensuite nos plugins directement dans le répertoire `.vim/bundle` que vous allez vous empresser de créer de cette manière :

.. code-block:: bash

    # Creation du repertoire bundle
    mkdir -p ~/.vim/bundle

Il ne vous reste plus qu'à activer pathogen dans votre |vimrc| et le tour est joué. Nous placerons le code listé ci-dessous au début du fichier |vimrc|, directement après la ligne `set nocompatible`. Il est impératif de placer le code **au début** de votre fichier |vimrc|, sinon ça ne marchera pas.::

    " Activation de pathogen
    call pathogen#infect()

Puisque charité bien ordonnée commence par soi-même, nous allons ranger notre petit plugin *Solarized* en utilisant *Pathogen*. Il nous suffit de créer un répertoire `solarized` dans notre répertoire `bundle` fraîchement créé. Vous pouvez l'appeler comme vous le souhaitez, tout sous-répertoire du répertoire `bundle` sera considéré comme un répertoire de plugin. Nous déplaçons ensuite le répertoire `colors` dans le répertoire `solarized` comme ceci :

.. code-block:: bash

    # Creation du repertoire pour solarized
    mkdir ~/.vim/bundle/solarized
    # Et hop un peu de rangement
    mv ~/.vim/colors ~/.vim/bundle/solarized

Actuellement, Pathogen reste encore le gestionnaire de plugins |vim| le plus utilisé. Mais depuis peu, un challenger est arrivé, il s'appelle Vundle https://github.com/gmarik/vundle. J'ai choisi de vous présenter Pathogen car c'est de lui que vous entendrez le plus parler, mais sachez que Vundle est aussi une alternative intéressante : il est compatible avec Pathogen et il gère les versions et les mises à jours de vos plugins directement depuis internet. Pour ceux qui connaissent Ruby, c'est le Bundler (http://gembundler.com/) pour |vim|.


Voilà notre |vim| est presque prêt pour le grand bain. Il vous reste une petite étape à franchir : disposer d'un moyen pratique pour explorer les fichiers d'un projet. C'est ici que *The NERD Tree* entre en lice.

.. _secnerdtree:

Explorateur de fichiers : The NERD Tree
---------------------------------------

The NERD Tree est un plugin permettant d'afficher visuellement une arborescence de fichiers directement dans la partie gauche (par défaut) de votre |vim|, à la *TextMate*, *Sublime Text* ou encore *Eclipse/NetBeans*. Ce plugin n'est pas essentiel si vous souhaitez tout contrôler au clavier (je ne l'utilise plus moi-même), mais est assez pratique lorsque l'on débute avec |vim|.

L'alternative que nous verrons plus tard au chapitre :ref:`plugins` est d'utiliser les plugin *Ctrl-p* ou *Command-t* pour trouver des fichiers et les plugins *LustyExplorer* et *LustyJuggler* pour naviguer entre les fichiers. En effet, devoir visualiser l'arborescence pour trouver un fichier est toujours plus lent que de trouver le fichier à partir de son nom par exemple. The NERD Tree vous permettra donc d'obtenir un |vim| se comportant comme un éditeur classique avec un explorateur de fichiers sur lequel vous pourrez cliquer.

Nous allons tout d'abord préparer *Pathogen* pour installer les différents fichiers de *The NERD Tree*.

.. code-block:: bash

    # Creation du repertoire pour The NERD Tree
    mkdir ~/.vim/bundle/nerdtree

Téléchargez ensuite le dernier *.zip* disponible sur la page du plugin http://www.vim.org/scripts/script.php?script_id=1658. À l'heure où j'écris ces lignes, la dernière version disponible est la version 4.2.0 que vous pouvez télécharger à cette adresse : http://www.vim.org/scripts/download_script.php?src_id=17123.

Ouvrez le fichier zip et placez son contenu dans le répertoire ``~/.vim/bundle/nerdtree`` que nous venons de créer. Vous devriez avoir une arborescence ressemblant à celle ci-dessous pour votre répertoire ``nerdtree`` :

.. code-block:: html

    nerdtree
    |-- doc
    |   `-- NERD_tree.txt
    |-- nerdtree_plugin
    |   |-- exec_menuitem.vim
    |   `-- fs_menu.vim
    |-- plugin
    |   `-- NERD_tree.vim
    `-- syntax
        `-- nerdtree.vim

Il va ensuite falloir activer le plugin. Vous pouvez le faire manuellement en tapant :vimcmd:`:NERDTree` en mode normal. Si vous préférez activer *The NERD Tree* à chaque fois que vous ouvrez votre |vim|, ajoutez ces lignes dans votre |vimrc|: ::

    " Activation de NERDTree au lancement de vim
    autocmd vimenter * NERDTree

C'est, j'en conviens, une commande un peu barbare qui pourrait se traduire en bon vieux français par : à chaque ouverture de vim (``vimenter``), peu importe le type de fichier (``*``), lancer *The NERD Tree* (``NERDTree``).

Rien de particulier ensuite, *The NERD Tree* vous affiche l'arborescence du répertoire où vous avez lancé |vim|, comme vous le montre la capture d'écran ci-dessous. Vous pouvez utiliser la souris et/ou le clavier pour vous déplacer. 

.. figure:: ../book-tex/graphics/vim-nerdtree.png

   |vim| avec *The NERD Tree* d'activé.

Vous pouvez aussi effectuer des commandes (créer, copier des fichiers) en appuyant sur |ttm| lorsque vous êtes dans *The NERD Tree*. Pour passer de la fenêtre de *NERD Tree* à la fenêtre d'édition de votre fichier au clavier, appuyez sur ``Ctrl + w`` puis ``w``. C'est à dire la touche ``Control (Ctrl)`` et tout en la laissant appuyée la touche ``w``. Vous pouvez ensuite tout lâcher pour appuyer une nouvelle fois sur ``w``. Ce raccourci clavier sera d'ailleurs toujours valable pour naviguer entre vos différentes fenêtres |vim| (il n'est pas spécifique à *The NERD Tree*).


Nous voilà fin prêts
====================

Voilà, vous avez fait le plus dur. Enfin presque. Nous venons de couvrir ce qui manque cruellement à |vim| : une configuration par défaut acceptable. Je ne dis pas que c'est la panacée pour l'instant, mais ça devrait vous permettre d'avoir un |vim| utilisable comme n'importe quel autre éditeur de texte dont vous ne connaissez pas encore toutes les possibilités. Je vous recommande à ce stade de commencer à l'utiliser dans votre vie quotidienne. N'hésitez pas à user et à abuser de la souris et des différents menus qui sont à votre disposition. Le but ici étant de réduire l'impact de l'utilisation de |vim| sur votre travail quotidien. Ce n'est pas encore le temps de briller en société. Vous apprendrez les raccourcis clavier au fur et à mesure, et ça ne fait pas de vous un utilisateur de |vim| de seconde zone. Il faut bien commencer un jour.

Nous allons maintenant aborder ce qui fait l'unicité de |vim| : sa gestion des modes et des commandes pour manipuler le texte. La balle est dans votre camp maintenant : ou vous êtes prêt à changer vos habitudes et à passer à un autre niveau d'efficacité, ou alors n'utiliser |vim| que comme un bloc-notes amélioré vous convient (dans ce cas là, vous pouvez vous arrêter là). C'est vous qui voyez !