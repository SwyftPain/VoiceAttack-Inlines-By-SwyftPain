# VoiceAttack Inlines
 C# inline functions for VoiceAttack

MySQL inline not precompiled due to the requirement of editing the values.

``using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using MySql.Data.MySqlClient;

public class VAInline
{
    public void main()
    {

      // This is my connection string i have assigned the database file address path 
      string connetionString = null;
      // Assign database details
      connetionString = "server=localhost;database=dbname;uid=username;pwd=password;";

      using (MySqlConnection cn = new MySqlConnection(connetionString))
        {
        try
          {
          // change the table and values, divide values by comma
          string query = "INSERT INTO table(Value) VALUES (?value);";
          cn.Open();
          using (MySqlCommand cmd = new MySqlCommand(query, cn))
          {
            // change value, type from "VarChar" to your input type and add your variable. For multiple, just copy/paste and edit parameters
            cmd.Parameters.Add("?value", MySqlDbType.VarChar).Value = VA.GetText("textvariable");
            cmd.ExecuteNonQuery();
          }
      }
          catch (MySqlException ex)
      {
          MessageBox.Show("Error in adding mysql row. Error: "+ex.Message);
      }
    }
  }
}``
