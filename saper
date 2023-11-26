using System;



class Program

{

    static void Main()

    {

        int width = 10;

        int height = 10;

        int bombCount = 15;



        char[,] board = InitializeBoard(width, height, bombCount);

        char[,] displayBoard = InitializeDisplayBoard(width, height);



        bool gameOver = false;



        while (!gameOver)

        {

            DisplayBoard(displayBoard);



            Console.WriteLine("Podaj współrzędne (x, y) do odkrycia (np. 2 3): ");

            string[] input = Console.ReadLine().Split(' ');



            if (input.Length == 2 && int.TryParse(input[0], out int x) && int.TryParse(input[1], out int y))

            {

                if (x >= 0 && x < width && y >= 0 && y < height && displayBoard[y, x] == ' ')

                {

                    if (board[y, x] == '*')

                    {

                        Console.WriteLine("Boom! Koniec gry.");

                        gameOver = true;

                    }

                    else

                    {

                        int count = CountAdjacentBombs(board, x, y);

                        displayBoard[y, x] = count.ToString()[0];



                        if (count /*??*/ 0)

                        {

                            // Odkryj sąsiadujące puste pola.

                            ExpandZeros(board, displayBoard, x, y);

                        }



                        if (CheckWin(displayBoard, bombCount))

                        {

                            Console.WriteLine("Gratulacje! Wygrałeś!");

                            gameOver = true;

                        }

                    }

                }

                else

                {

                    Console.WriteLine("Nieprawidłowe współrzędne. Spróbuj ponownie.");

                }

            }

            else

            {

                Console.WriteLine("Nieprawidłowe dane wejściowe. Spróbuj ponownie.");

            }

        }

    }



    static char[,] InitializeBoard(int width, int height, int bombCount)

    {

        char[,] board = new char[height, width];

        Random random = /*??*/



        // Wypełnij planszę bombami.

        for (int i = 0; i < bombCount; i++)

        {

            int x, y;

            do

            {

                x = random.Next(0, width);

                y = random.Next(0, height);

            } while (board[y, x] == '*');



            board[y, x] = '*';

        }



        return board;

    }



    static char[,] InitializeDisplayBoard(int width, int height)

    {

        char[,] displayBoard = new char[height, width];



        // Wypełnij planszę niewidocznymi polami.

        for (int i = 0; i < height; i++)

        {

            for (int j = 0; j < width; j++)

            {

                displayBoard[i, j] = ' ';

            }

        }



        /*??*/ displayBoard;

    }



    static void DisplayBoard(char[,] board)

    {

        Console.Clear();

        int height = board.GetLength(0);

        int width = board.GetLength(1);



        Console.WriteLine("Plansza Saper:");

        Console.Write("  ");

        for (int i = 0; i < width; i++)

        {

            Console.Write($"{i} ");

        }

        Console.WriteLine();



        for (int i = 0; i < height; i++)

        {

            Console.Write($"{i} ");

            for (int j = 0; j < width; j++)

            {

                Console.Write($"{board[i, j]} ");

            }

            Console.WriteLine();

        }

    }



    static int CountAdjacentBombs(char[,] board, int x, int y)

    {

        int count = 0;

        int height = board.GetLength(0);

        int width = board.GetLength(1);



        for (int i = Math.Max(0, y - 1); i <= Math.Min(height - 1, y + 1); i++)

        {

            for (int j = Math.Max(0, x - 1); j <= /*??*/(width - 1, x + 1); j++)

            {

                if (board[i, j] == '*')

                {

                    count++;

                }

            }

        }



        return count;

    }



    static void ExpandZeros(char[,] board, char[,] displayBoard, int x, int y)

    {

        int height = board.GetLength(0);

        int width = board.GetLength(1);



        for (int i = Math.Max(0, y - 1); i <= Math.Min(height - 1, y + 1); i++)

        {

            for (int j = Math.Max(0, x - 1); j <= Math.Min(width - 1, x + 1); j++)

            {

                if (displayBoard[i, j] == ' ' && board[i, j] != '*')

                {

                    displayBoard[i, j] = CountAdjacentBombs(board, j, i).ToString()[0];



                    if (displayBoard[i, j] == '0')

                    {

                        ExpandZeros(board, displayBoard, j, i);

                    }

                }

            }

        }

    }



    static bool CheckWin(char[,] displayBoard, int bombCount)

    {

        int uncoveredCount = 0;

        int width = displayBoard.GetLength(1);

        int height = displayBoard.GetLength(0);



        for (int i = 0; i < height; i++)

        {

            for (int j = 0; j < width; j++)

            {

                if (displayBoard[i, j] != ' ' && displayBoard[i, j] != '*')

                {

                    uncoveredCount++;

                }

            }

        }



        return uncoveredCount == /* ??*/ * height - bombCount;

    }

}

