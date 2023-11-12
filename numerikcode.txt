import time

def f1(x):
    return x ** 2 - 20

def det_f1(x):
    return 2 * x

def newton_raphson(func, d_func, x, tolerence, max_iterations, real_root=None):
    if d_func(x) == 0:
        print("Newton-Raphson gagal dijalankan.")
        return None
    else:
        iterations = 1
        start_time = time.time()
        while abs(func(x) / d_func(x)) >= tolerence and iterations <= max_iterations:
            current_iteration_print = "Iterasi : {0}".format(iterations)
            if func(x) == 0:
                print(current_iteration_print + "Solusi ditemukan : {0}".format(x))
                return x
            
            x = x - func(x) / d_func(x)
            if d_func(x) == 0:
                print("Newton-Raphson gagal dijalankan.")
                return None
            current_iteration_print += ", {0}".format(x)
            iterations = iterations + 1

            end_time = time.time()
            elapsed_time = end_time - start_time
            current_iteration_print += ", Waktu per Iterasi: {0} detik".format(elapsed_time)

            print(current_iteration_print)
        
        print("\nJumlah iterasi : ", iterations)
        print("Hasil akhir : ", x)

        
print(newton_raphson(f1, det_f1, 1.5, 0.00001, 30, 1))