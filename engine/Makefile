# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: ablizniu <marvin@42.fr>                    +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2019/03/08 12:28:56 by yalytvyn          #+#    #+#              #
#    Updated: 2019/06/23 15:27:42 by ablizniu         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

NAME	= doom

NAMEDB	= doon_db

SRC		=	src/collision_2.c src/collision.c src/cr_cols_init.c src/draw_1.c \
			src/draw_2.c src/draw.c src/drawsector_1.c src/drawsector.c src/init.c \
			src/key.c src/key_2.c src/lava_and_health_bar.c src/ligth.c src/lst_utils.c \
			src/main.c src/mapping.c src/mapping_2.c src/mouse.c src/parse_utils.c \
			src/parse_utils_2.c src/parse_utils_3.c src/parse_utils_4.c src/parse_utils_5.c \
			src/parse_validation.c src/parse_validation_2.c src/parse_validation_3.c \
			src/parse_validation_4.c src/player_transform.c src/player_transform_2.c \
			src/print.c src/ray.c src/ray_2.c src/resourse.c src/sdlmain.c src/shooting.c \
			src/sky.c src/sprite.c src/start_menu.c src/utils.c

SDL2_HEADER =	-I ./../frameworks/SDL2.framework/Headers/ \
				-I ./../frameworks/SDL2_mixer.framework/Headers/ \
				-I ./../frameworks/SDL2_ttf.framework/Headers/

SDLFLAGS = -framework SDL2 -framework SDL2_mixer -framework SDL2_ttf -F ../frameworks

OPT = -O3 -flto -pipe -Ofast -march=native -mtune=native
DB = -g

SDL2_P = -rpath @loader_path/../frameworks/

OBJ		= $(patsubst src/%.c,obj/%.o,$(SRC))

.SILENT:

all: $(NAME)

$(NAME): $(OBJ)
	make -C ../libft/
	gcc -Wall -Wextra $(OPT) -flto -pipe -Ofast -march=native -mtune=native -L ../libft/ -lft -L/usr/local/lib -I includes -I  ../libft/includes $(SDL2_HEADER) $(SDL2_P) $(SDLFLAGS) $(SRC)  -o $(NAME)
	printf '\033[32m[ ✔ ] %s\n\033[0m' "Create Dooms"

obj/%.o: src/%.c
	mkdir -p obj
	gcc  -Wall -Wextra -c $(OPT) -Iincludes -I../libft/includes $(SDL2_HEADER) $< -o $@

db: $(NAMEDB)
$(NAMEDB): $(OBJ)
	make -C ../libft/
	gcc -Wall -Wextra $(DB) -L ../libft/ -lft -L/usr/local/lib -I ../includes -I ../libft/includes $(SDL2_HEADER) $(SDL2_P) $(SDLFLAGS) $(SRC)  -o $(NAME)
	printf '\033[32m[ ✔ ] %s\n\033[0m' "Create Dooms_db"

obj/%.o: src/%.c
	mkdir -p obj
	gcc  -Wall -Wextra -c $(DB) -I includes -I ../libft/includes $(SDL2_HEADER) $< -o $@


clean:
	/bin/rm -rf obj/
	make -C ../libft/ clean

fclean: clean
	/bin/rm -f $(NAME)
	make -C ../libft/ fclean

re: fclean all

test: re
	printf '\033[32m%s\n\033[0m' "-------------------------------------"
	./doom3d

all: $(NAME)
.PHONY: clean fclean re all