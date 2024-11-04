# Random-Password-Generator C#

This programme creates a random strong passwords mixing upper and lower case, symbols and numbers.
Extension: 
• Have the password also use ASCII characters 
• Have the passwords stored in an external file 

    using System;
    using System.Collections.Generic;
    using System.ComponentModel;
    using System.Data;
    using System.Drawing;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows.Forms;
    using System.IO;
    
    namespace Random_Password_generator
    {
        public partial class Form1 : Form
        {
    
            List<string> password = new List<string>();
            public const string filepathway = @"C:\Users\vanys\OneDrive\Desktop\Computer_science\VIRTUALSTUDIO\Random Password generator\Random Password generator\PasswordStore.txt";
            public string Raw_Password; 
            public Form1()
            {
                InitializeComponent();
                No_btn.Hide();
                question.Hide();
                Yes_btn.Hide();
            }
    
            private void gen_password_Click(object sender, EventArgs e)
            {
                password.Clear();
    
                Random random = new Random();
    
                for (int i = 0; i < 8; i++)
                {
                    char[] allcharacters = "1234567890-=`QWERTYUIOPASDFGHJKLZXCVBNMqwertyuiopasdfghjklzxcvbnm!£$%^&*()';:{}[]#~<>,.?/_+|@¬".ToCharArray();
                    password.Add(allcharacters[random.Next(allcharacters.Length)].ToString());
                }
                string raw_pas = string.Join("", password);
                word_pass.Text = raw_pas;
                Raw_Password = raw_pas;
                gen_password.Enabled = false;
                No_btn.Show();
                question.Show();
                Yes_btn.Show();
                
            }
    
            private void No_btn_Click(object sender, EventArgs e)
            {
                No_btn.Hide();
                question.Hide();
                Yes_btn.Hide();
                gen_password.Enabled = true;
                word_pass.Clear();
            }
    
            private void Yes_btn_Click(object sender, EventArgs e)
            {
                File.AppendAllText(filepathway, Raw_Password + '\n');          
                No_btn.Hide();
                question.Hide();
                Yes_btn.Hide();
                word_pass.Clear();
                gen_password.Enabled = true;
                MessageBox.Show("Password Saved.");
            }
    
            private void label1_Click(object sender, EventArgs e)
            {
    
            }
    
        }
    }
