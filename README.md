# Simple-2D-game-engine  

Функционал движка:

1. Создание примитивных объектов (Типа круга, прямоугольника и других) и их обработка (коллизии, выключение, поворот, позиция и тп).

2. Создание кнопок (по факту примитивный объект, с навешенным на него функционалом).

3. Камера (по крайней мере её можно будет перемещать).

4. Обработка текста.

5. Возможно добавить звук.


# macOS
Install Vulkan SDK
https://vulkan.lunarg.com/sdk/home#mac

```bash
echo "Install dependencies"
brew install glfw cmake

echo "Clone repository"
git clone https://github.com/Gnihtone/Simple-2D-game-engine.git
cd Simple-2D-game-engine/src

echo "Compile shaders"
mkdir -p build/shaders
glslc shader.vert -o build/shaders/vert.spv
glslc shader.frag -o build/shaders/frag.spv

echo "Compile program"
cd build
cmake ..
make

echo "Run program"
./run
```
